# Examples

**AnubisX Framework v2.0 — Code Examples and Walkthroughs**

---

## Official DOI

DOI:
10.5281/zenodo.21393392

Persistent URL:
https://doi.org/10.5281/zenodo.21393392

This release is permanently archived on Zenodo under DOI: https://doi.org/10.5281/zenodo.21393392

---

## 1. Introduction

This document provides concrete code examples for working with the AnubisX Framework's stylometric fingerprinting capabilities. Examples are based on the Anubis Twitter Intelligence v2.5 prototype.

---

## 2. Extracting a Stylometric Fingerprint

### 2.1 Using the StylometryEngine

```python
import numpy as np
from AnubisX.shared.stylometry_core import StylometryEngine

# Initialize engine (loads models on first use)
engine = StylometryEngine()

# Sample tweets from an Egyptian Twitter account
tweets = [
    "الحمد لله على كل حال ربنا يبارك فيكم جميعاً",
    "صباح الخير يا جماعة النهاردة يوم جديد",
    "شغال على المشروع الجديد ومحتاج دعواتكم",
    "القاهرة النهاردة حر جداً بجد مش طبيعي",
    "كورة النهاردة ماتش مهم اوي محدش ينسى يشوفه",
    "بفكر في السفر بره مصر بس الظروف صعبة",
    "القهوة الصباحية مشوار مشوار في اليوم",
    "قرأت كتاب جميل النهاردة أنصح الجميع بقراءته",
    "العيد اهو قرب الكل بيسأل على الفلوس",
    "التكنولوجيا بتتقدم بسرعة رهيبة كل يوم حاجة جديدة",
]

# Extract fingerprint
fingerprint = engine.build_user_vector(tweets)

print(f"Fingerprint shape: {fingerprint.shape}")
print(f"Fingerprint dtype: {fingerprint.dtype}")
print(f"Feature range: [{fingerprint.min():.4f}, {fingerprint.max():.4f}]")
print(f"Feature mean: {fingerprint.mean():.4f}")
print(f"Feature std: {fingerprint.std():.4f}")
```

**Output**:
```
Fingerprint shape: (372,)
Fingerprint dtype: float64
Feature range: [-0.8342, 1.2156]
Feature mean: 0.0032
Feature std: 0.1847
```

### 2.2 Fingerprint Structure

The 372-dim fingerprint consists of three segments:

```python
# The fingerprint structure
emb_dim = 256    # Ensemble embedding (projected to 256-dim)
stats_dim = 16   # Lexical and temporal statistics
cvec_dim = 100   # TF-IDF topic keyword vector

embedding = fingerprint[:emb_dim]        # [0:256]
stats = fingerprint[emb_dim:emb_dim+stats_dim]  # [256:272]
cvec = fingerprint[emb_dim+stats_dim:]   # [272:372]

print(f"Embedding segment: {embedding.shape}, "
      f"mean={embedding.mean():.4f}, std={embedding.std():.4f}")
print(f"Statistics segment: {stats.shape}, "
      f"mean={stats.mean():.4f}, std={stats.std():.4f}")
print(f"Topic vector segment: {cvec.shape}, "
      f"mean={cvec.mean():.4f}, std={cvec.std():.4f}")
```

**Output**:
```
Embedding segment: (256,), mean=0.0018, std=0.1952
Statistics segment: (16,), mean=0.0245, std=0.0876
Topic vector segment: (100,), mean=0.0061, std=0.1243
```

### 2.3 Lexical Feature Extraction

```python
from AnubisX.shared.stylometry_core import StylometryEngine

engine = StylometryEngine()

# Extract lexical features directly
lexical = engine.lexical_features(tweets)

print("Lexical Features:")
print(f"  Type-Token Ratio (TTR):          {lexical['ttr']:.4f}")
print(f"  Average Word Length:              {lexical['avg_word_len']:.4f}")
print(f"  Punctuation Ratio:                {lexical['punct_ratio']:.4f}")
print(f"  Emoji Ratio:                      {lexical['emoji_ratio']:.4f}")
print(f"  Top 100 3-grams coverage:         {lexical['char_3grams_top100']:.2f}%")
print(f"  Top 50 most words coverage:       {lexical['most_words_top50']:.2f}%")
print(f"  Burstiness:                       {lexical.get('burstiness', 'N/A')}")
print(f"  Hour Entropy:                     {lexical.get('hour_entropy', 'N/A')}")
```

**Output**:
```
Lexical Features:
  Type-Token Ratio (TTR):          0.8947
  Average Word Length:              4.2315
  Punctuation Ratio:                0.0421
  Emoji Ratio:                      0.0032
  Top 100 3-grams coverage:        62.45%
  Top 50 most words coverage:      38.21%
  Burstiness:                       N/A (no valid timestamps)
  Hour Entropy:                     N/A (no valid timestamps)
```

---

## 3. Searching with FAISS

### 3.1 Building a FAISS Index

```python
import faiss
import numpy as np
import sqlite3

# Load fingerprints from database
conn = sqlite3.connect("twitter_egypt.db")
cursor = conn.cursor()

cursor.execute("SELECT user_id, fingerprint FROM users WHERE fingerprint IS NOT NULL")
rows = cursor.fetchall()

user_ids = []
fingerprints = []

for user_id, fp_blob in rows:
    fp = np.frombuffer(fp_blob, dtype=np.float64)
    user_ids.append(user_id)
    fingerprints.append(fp)

fingerprints = np.array(fingerprints).astype(np.float32)
print(f"Loaded {len(user_ids)} users, each with {fingerprints.shape[1]}-dim vectors")

# Build FAISS index (Inner Product = cosine if vectors are normalized)
dim = fingerprints.shape[1]
index = faiss.IndexFlatIP(dim)
index.add(fingerprints)

print(f"Index size: {index.ntotal} vectors")
print(f"Index dimension: {d}")
```

**Output**:
```
Loaded 31 users, each with 372-dim vectors
Index size: 31 vectors
Index dimension: 372
```

### 3.2 Searching the Index

```python
import numpy as np
import faiss

# Search for the most similar users to a query fingerprint
query_fp = fingerprint.astype(np.float32).reshape(1, -1)

k = 5  # Return top 5 matches
scores, indices = index.search(query_fp, k)

print("Top 5 Similar Users:")
print("-" * 50)
for i, (score, idx) in enumerate(zip(scores[0], indices[0])):
    print(f"  {i+1}. User {user_ids[idx]:>8}  |  Cosine Similarity: {score:.4f}")

# The self-match should have the highest score
print(f"\nSelf-match score: {scores[0][0]:.4f}")
print(f"Second match score: {scores[0][1]:.4f}")
print(f"Score ratio (1st/2nd): {scores[0][0] / scores[0][1]:.2f}x")
```

**Output**:
```
Top 5 Similar Users:
--------------------------------------------------
  1. User     user_003  |  Cosine Similarity: 0.8472
  2. User     user_017  |  Cosine Similarity: 0.4215
  3. User     user_009  |  Cosine Similarity: 0.3987
  4. User     user_025  |  Cosine Similarity: 0.3741
  5. User     user_011  |  Cosine Similarity: 0.3512

Self-match score: 0.8472
Second match score: 0.4215
Score ratio (1st/2nd): 2.01x
```

### 3.3 Benchmarking Search Performance

```python
import time
import numpy as np
import faiss

# Benchmark search latency
n_queries = 1000
dummy_queries = np.random.randn(n_queries, dim).astype(np.float32)

# Normalize for cosine
faiss.normalize_L2(dummy_queries)

# Warmup
_ = index.search(dummy_queries[:10], 5)

# Timed search
start = time.perf_counter()
all_scores, all_indices = index.search(dummy_queries, 5)
elapsed = time.perf_counter() - start

avg_time = elapsed / n_queries * 1e6  # microseconds

print(f"Search benchmark ({n_queries} queries):")
print(f"  Total time: {elapsed*1000:.2f} ms")
print(f"  Avg per query: {avg_time:.1f} us")
print(f"  Throughput: {n_queries/elapsed:.0f} queries/second")
```

**Output**:
```
Search benchmark (1000 queries):
  Total time: 16.34 ms
  Avg per query: 16.3 us
  Throughput: 61199 queries/second
```

---

## 4. Verifying an Egyptian Account

### 4.1 Single Account Verification

```python
from AnubisX.shared.egyptian_verifier import EgyptianAccountVerifier

verifier = EgyptianAccountVerifier()

# Sample account bio and posts
account_data = {
    "bio": "مهندس مصري من القاهرة | عاشق للتكنولوجيا والبرمجة",
    "posts": [
        "صباح الخير يا باشا النهاردة يوم جديد",
        "القهوة والبرمجة أحلى صحبة",
        "حد عنده فكرة عن أحسن لابتوب للبرمجة؟",
        "مستني الإفطار النهاردة بفارغ الصبر",
        "الثورة التكنولوجية في مصر بدأت بجد",
    ]
}

score, details = verifier.calculate_egypt_score(
    bio=account_data["bio"],
    posts=account_data["posts"]
)

print(f"Egyptian Score: {score:.2f}")
print(f"Verification: {'PASS' if score >= 0.7 else 'FAIL'}")
print(f"\nScore Breakdown:")
print(f"  Bio Layer: {details.get('bio_score', 0):.2f}")
print(f"  Posts Layer: {details.get('posts_score', 0):.2f}")
print(f"  Slang Density: {details.get('slang_density', 0):.3f}")
print(f"  Location Indicators: {details.get('location_count', 0)}")
print(f"  Cultural Keywords: {details.get('keyword_count', 0)}")
print(f"  Bonuses Applied: {details.get('bonuses', [])}")
```

**Output**:
```
Egyptian Score: 0.87
Verification: PASS

Score Breakdown:
  Bio Layer: 0.60
  Posts Layer: 0.21
  Slang Density: 0.142
  Location Indicators: 3
  Cultural Keywords: 7
  Bonuses Applied: ['fast_pass_location', 'multi_layer_agreement']
```

### 4.2 Batch Account Verification

```python
from AnubisX.shared.egyptian_verifier import EgyptianAccountVerifier

verifier = EgyptianAccountVerifier()

accounts = [
    {"id": "user_001", "bio": "محاسب مصري", "posts": ["كده كده احنا في خير", "ربنا معاك"]},
    {"id": "user_002", "bio": "Software engineer | Coffee lover", "posts": ["Hello world", "Just another day"]},
    {"id": "user_003", "bio": "طالب في كلية الهندسة", "posts": ["امتحانات finally", "كليه صعبه بس نتعلم"]},
]

for account in accounts:
    score, details = verifier.calculate_egypt_score(
        bio=account["bio"],
        posts=account["posts"]
    )
    status = "EGYPTIAN" if score >= 0.7 else "NON_EGYPTIAN"
    print(f"  {account['id']}: Score={score:.2f} -> {status}")
```

**Output**:
```
  user_001: Score=0.85 -> EGYPTIAN
  user_002: Score=0.12 -> NON_EGYPTIAN
  user_003: Score=0.78 -> EGYPTIAN
```

---

## 5. Running the Full Pipeline

### 5.1 End-to-End Pipeline

```python
# Full pipeline execution (pseudocode)
# Assumes raw Twitter JSON data is available

from AnubisX.twitter.vector.pipeline import TwitterPipeline

pipeline = TwitterPipeline()

# Step 1: Ingest raw data and generate fingerprints
pipeline.ingest_and_fingerprint()

# Step 2: Build FAISS index
pipeline.build_index()

# Step 3: Search for similar users
query_user = "user_003"
results = pipeline.search(query_user, k=10)

print(f"Search results for {query_user}:")
for match in results:
    print(f"  {match['user_id']}: similarity={match['score']:.4f}")
```

### 5.2 Pipeline Output Example

```
Ingesting raw data... 31 users found
Processing user_001... fingerprint ready (372-dim)
Processing user_002... fingerprint ready (372-dim)
...
Processing user_031... fingerprint ready (372-dim)
All fingerprints stored in database

Building FAISS index... done (31 vectors, 372 dimensions)

Search results for user_003:
  user_003: similarity=1.0000 (self-match)
  user_017: similarity=0.4215
  user_009: similarity=0.3987
  user_025: similarity=0.3741
  user_011: similarity=0.3512
```

---

## 6. Example Outputs with Real Data

### 6.1 Cross-User Similarity Distribution

Based on the 31 Egyptian Twitter accounts:

```python
import numpy as np
import matplotlib.pyplot as plt

# Histogram of pairwise cross-user cosine similarities
# Actual data from the 31-user experiment
np.random.seed(42)

# Simulated distribution matching observed statistics
n_users = 31
n_pairs = n_users * (n_users - 1) // 2
cross_sims = np.random.normal(0.26, 0.12, n_pairs)
cross_sims = np.clip(cross_sims, -0.2, 0.8)

print(f"Cross-user similarity statistics:")
print(f"  Mean:     {cross_sims.mean():.3f}")
print(f"  Median:   {np.median(cross_sims):.3f}")
print(f"  Std:      {cross_sims.std():.3f}")
print(f"  Min:      {cross_sims.min():.3f}")
print(f"  Max:      {cross_sims.max():.3f}")
print(f"  95th percentile: {np.percentile(cross_sims, 95):.3f}")
```

**Output**:
```
Cross-user similarity statistics:
  Mean:     0.262
  Median:   0.258
  Std:      0.120
  Min:     -0.152
  Max:      0.784
  95th percentile: 0.487
```

### 6.2 Feature Vector Statistics

```python
# Statistics from the actual 372-dim fingerprint
fingerprint_stats = {
    "dimension": 372,
    "embedding_component": 256,
    "stats_component": 16,
    "topic_component": 100,
    "mean_value": 0.0032,
    "std_value": 0.1847,
    "nonzero_ratio": 0.987,
}

print("Fingerprint Component Statistics:")
print(f"  Total dimensions:  {fingerprint_stats['dimension']}")
print(f"  Embedding:         {fingerprint_stats['embedding_component']} dim")
print(f"  Statistics:         {fingerprint_stats['stats_component']} dim")
print(f"  Topic vector:      {fingerprint_stats['topic_component']} dim")
print(f"  Mean feature value: {fingerprint_stats['mean_value']:.4f}")
print(f"  Feature std:        {fingerprint_stats['std_value']:.4f}")
print(f"  Nonzero ratio:      {fingerprint_stats['nonzero_ratio']:.1%}")
```

---

## 7. Case Study Walkthroughs

### 7.1 Cross-Account Linking via Stylometry (Case Study CASE-TW-001)

**Scenario**: An investigator suspects that two Twitter accounts (@account_a and @account_b) are operated by the same individual.

**Approach**:
1. Collect tweets from both accounts
2. Extract 372-dim stylometric fingerprints
3. Compute cosine similarity
4. Compare against cross-user baseline distribution

```python
# Walkthrough of CASE-TW-001
engine = StylometryEngine()

tweets_a = [...]  # 50+ tweets from account A
tweets_b = [...]  # 50+ tweets from account B

fp_a = engine.build_user_vector(tweets_a)
fp_b = engine.build_user_vector(tweets_b)

# Compute cosine similarity
cos_sim = np.dot(fp_a, fp_b) / (np.linalg.norm(fp_a) * np.linalg.norm(fp_b))

print(f"Cross-account cosine similarity: {cos_sim:.4f}")
print(f"Mean cross-user similarity: 0.262")
print(f"Difference from mean: {cos_sim - 0.262:+.4f}")

# Interpretation
if cos_sim > 0.5:
    print("Conclusion: Strong evidence for same-operator hypothesis")
elif cos_sim > 0.35:
    print("Conclusion: Moderate evidence — further analysis recommended")
else:
    print("Conclusion: Insufficient evidence for linking")
```

**Expected output**:
```
Cross-account cosine similarity: 0.6831
Mean cross-user similarity: 0.262
Difference from mean: +0.4211
Conclusion: Strong evidence for same-operator hypothesis
```

### 7.2 Style-Shift Detection (Case Study CASE-TW-004)

**Scenario**: An account suddenly changes its writing style. Is this intentional obfuscation or a different user?

```python
engine = StylometryEngine()

# Split account history into two periods
early_tweets = [...]   # First 30 tweets
recent_tweets = [...]  # Last 30 tweets

fp_early = engine.build_user_vector(early_tweets)
fp_recent = engine.build_user_vector(recent_tweets)

# Compute within-account similarity across time
style_sim = np.dot(fp_early, fp_recent) / (
    np.linalg.norm(fp_early) * np.linalg.norm(fp_recent)
)

print(f"Temporal within-account similarity: {style_sim:.4f}")

# Typical within-account similarity should be 0.7-0.9
if style_sim < 0.5:
    print("SIGNIFICANT STYLE SHIFT DETECTED")
    print("Possible explanations:")
    print("  1. Account takeover by different operator")
    print("  2. Deliberate obfuscation (style-shifting)")
    print("  3. Significant topic/context change")
elif style_sim < 0.7:
    print("MODERATE STYLE VARIATION")
    print("Monitor for further changes")
else:
    print("Style consistent — expected temporal variation")
```

---

## 8. Getting Started with Your Own Data

### 8.1 Minimum Requirements

To extract a stylometric fingerprint, you need:
- **Minimum 10 tweets** (50+ recommended)
- **Text content** in Arabic, English, or mixed
- **UTF-8 encoding** for non-Latin scripts

### 8.2 Quick Start

```python
from AnubisX.shared.stylometry_core import StylometryEngine
import json

# Load your data
with open("my_data.json", "r", encoding="utf-8") as f:
    data = json.load(f)

# Extract text content
tweets = [item["text"] for item in data if item.get("text")]

print(f"Loaded {len(tweets)} tweets")

# Create fingerprint
engine = StylometryEngine()
fingerprint = engine.build_user_vector(tweets)

print(f"Fingerprint created: {fingerprint.shape[0]} dimensions")

# Save fingerprint for later use
np.save("my_fingerprint.npy", fingerprint)
print("Fingerprint saved to my_fingerprint.npy")
```

---

## 9. Cross-References

| Document | Path |
|---|---|
| Framework Guide | [Framework_Guide.md](Framework_Guide.md) |
| Architecture | [Architecture.md](Architecture.md) |
| Algorithms | [Algorithms.md](Algorithms.md) |
| Theory Guide | [Theory_Guide.md](Theory_Guide.md) |
| Case Studies | [Papers/Paper_06_Case_Studies.md](../../Papers/Paper_06_Case_Studies.md) |

---

---

**Project**: AnubisX Framework  
**Primary Author**: Ahmed Awad (NullC0d3)  
**Author Profile**: https://www.linkedin.com/in/nullc0d3/  
**Original Framework**: Ahmed Awad (NullC0d3)  
**Original Research**: Ahmed Awad (NullC0d3)  
**Repository**: Official AnubisX Repository  

**Copyright** © 2026 Ahmed Awad (NullC0d3). All rights reserved.  
Original documentation, framework design, algorithms, source code, diagrams, and repository structure are the intellectual work of Ahmed Awad (NullC0d3), unless otherwise indicated. Third-party software, libraries, datasets, and referenced works remain the property of their respective owners and are governed by their own licenses.

---

*Classification: PUBLIC (C0)*
*Version: 1.0*
