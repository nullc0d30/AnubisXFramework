# AnubisX Framework v1.0 — Technical Deep-Dive

**Date:** 2026-07-15
**Classification:** PUBLIC (C0)
**Platform:** LinkedIn
**Word Count:** ~800

---

**Headline: AnubisX v1.0 — What the Numbers Actually Say (and Don't Say)**

Following the launch announcement, here is the technical deep-dive on what was validated, how, and where the gaps remain.

## The Architecture at a Glance

AnubisX processes social media text through four extractor modules that each capture a distinct dimension of writing style:

1. **Lexical** — word unigrams, bigrams, character n-grams (2-5), and part-of-speech tag distributions
2. **Syntactic** — sentence-level structure, punctuation patterns, function-word frequencies
3. **Structural** — message length distributions, paragraph breaks, formatting choices
4. **Content-Specific** — domain vocabulary, entity usage, topic markers

These four outputs are concatenated into a single 372-dimensional vector — the stylometric fingerprint.

## Validation Results

### Fingerprint Extraction
All four extractors executed successfully on 31 Egyptian Twitter accounts. The output dimensionality was verified at 372 features per user. No extraction errors occurred across the 15-experiment pipeline.

### Cosine-Similarity Search via FAISS
We built a FAISS `IndexFlatIP` index from the 31 fingerprint vectors. Query performance:

- **Average query time**: 16 microseconds (CPU, single thread)
- **Self-match recall**: 1.0 (each user's fingerprint is correctly their nearest neighbor)
- **Search type**: Exact inner-product (guaranteed correct ranking)

This is not a production benchmark — 31 vectors fits in L1 cache — but it validates the architecture. The same `IndexFlatIP` can be replaced with `IndexIVFFlat` or `IndexHNSWFlat` for GPU-accelerated large-scale deployment.

### Cross-User Differentiation
The 31×31 cosine-similarity matrix reveals a clear signal:

- **Mean cross-user similarity**: 0.26 (SD = 0.11)
- **Mean self-similarity**: > 0.80
- **Minimum self-similarity**: 0.61 (user with shortest tweet count)
- **Maximum cross-user similarity**: 0.63 (closest pair)

The separation between distributions is visually unambiguous (see heatmap in the prototype notebook), supporting the claim that these fingerprints capture user-specific stylistic patterns.

### Egyptian Arabic Content Analysis
Using a curated Egyptian Arabic keyword lexicon, we scanned all tweets for dialect markers:

- **Total keyword matches**: 5,127
- **Users with matches**: 31/31 (100%)
- **Mean matches per user**: 165.4 (SD = 89.2)
- **Most frequent category**: Egyptian slang particles (e.g., "إزاي", "كده", "بقي")

This validates both the dialect marker approach and demonstrates that Egyptian Arabic is sufficiently distinct in written social media text to warrant dialect-specific attribution methods.

## Where We're Transparent About Gaps

### Critical: Ensemble Embedding Blocked
The 3-model fusion layer (stylometric + MarBERT + AraBERT) is defined in the specification but non-functional. MarBERT and AraBERT return Hugging Face authentication errors. The file `05_Ensemble_Embedding.ipynb` documents the attempt and the error. Resolution requires a valid Hugging Face token or an alternative model source.

### Major: Temporal and Graph Layers Have No Data
The scraped dataset did not include:
- **Timestamps** — prevents temporal feature extraction (posting frequency, circadian patterns, burst detection)
- **Interaction metadata** (retweets, replies, mentions) — prevents social graph construction

Both layers are fully specified theoretically but have zero experimental validation.

### Major: No Ground Truth
We do not have a labeled evaluation set where authorship is independently verified. While cross-user differentiation is visually strong, we cannot report precision, recall, or F1 scores. This is the single most important gap for forensic applications.

## Reproducibility

All 12 Jupyter notebooks in the prototype (`03_PROTOTYPE/01_AnubisTwitterV2.5/`) can be executed in order on any machine with the dependencies listed in the requirements files. The normalized data and extracted feature vectors are included in the release.

## Bottom Line

Six of ten publication-ready claims are supported by experimental evidence. Four claims require additional data or authentication. We have a functioning foundation — not a finished product.

---

*For researchers: the data and code are available now. Run it, test it, break it. We want to know what happens when you do.*


