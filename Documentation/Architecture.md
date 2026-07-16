# Architecture

**AnubisX Framework v2.0 — Complete System Architecture**

---

## Official DOI

DOI:
10.5281/zenodo.21393392

Persistent URL:
https://doi.org/10.5281/zenodo.21393392

This release is permanently archived on Zenodo under DOI: https://doi.org/10.5281/zenodo.21393392

---

## 1. Overview

The AnubisX Framework implements a six-layer architecture for behavioral identity attribution. This document provides the complete architectural specification, covering layers, components, data flow, pipelines, workflows, fusion, and decision logic.

---

## 2. Six-Layer Architecture

```
┌──────────────────────────────────────────────────────────────────┐
│                        DECISION LAYER                           │
│     Attribution conclusions with quantified uncertainty          │
│     (identification, verification, inconclusive)                │
├──────────────────────────────────────────────────────────────────┤
│                       EVIDENCE LAYER                            │
│     Fusion, weighting, calibration, confidence estimation       │
│     (3 fusion strategies, Dempster-Shafer Theory)              │
├──────────────────────────────────────────────────────────────────┤
│                      COMPARISON LAYER                           │
│     Profile matching, similarity scoring (5 similarity funcs)   │
│     (1:N identification, 1:1 verification, forensic comparison)│
├──────────────────────────────────────────────────────────────────┤
│                       PROFILE LAYER                             │
│     Profile construction, normalization, Cognitive Centroid     │
│     estimation (multi-session aggregation, convergence)         │
├──────────────────────────────────────────────────────────────────┤
│                       FEATURE LAYER                             │
│     Feature extraction, signal decomposition, evidence          │
│     extraction (5 modalities, 100+ features total)              │
├──────────────────────────────────────────────────────────────────┤
│                        DATA LAYER                               │
│     Acquisition, validation, storage, preprocessing            │
│     (platform scrapers, quality gates, SQLite/FAISS)           │
└──────────────────────────────────────────────────────────────────┘
```

### 2.1 Layer Descriptions

#### Data Layer

The foundational layer responsible for all data acquisition, validation, and persistence.

**Components**:
- **DT-001**: Data Acquisition Interface — Platform-specific adapters for data collection
- **DT-002**: Data Validator — Quality checks, schema validation, P3 compliance
- **DT-003**: Data Store — SQLite persistence for profiles, feature vectors, metadata
- **DT-004**: Index Store — FAISS index for efficient similarity search

**Data flow**: Platform APIs/Scrapers → Data Validator → Data Store → Feature Layer

**Key constraints**:
- Minimum quality threshold for data acceptance (ALG-035)
- P3 Protocol proportionality constraints
- Schema versioning and migration support

#### Feature Layer

Transforms raw data into structured feature vectors for each behavioral modality.

**Components**:
- **FT-001**: Stylometric Extractor — Text → function-word frequencies, syntax patterns, lexical features
- **FT-002**: Chrono Extractor — Timestamps → circadian patterns, inter-event intervals, periodicity
- **FT-003**: Terminal Extractor — Interaction logs → command sequences, timing patterns, error patterns
- **FT-004**: Network Extractor — Social graph → topology metrics, centrality, community structure
- **FT-005**: Media Extractor — File metadata → organization patterns, naming conventions
- **FT-006**: Signal Decomposer — Separates cognitive signal from context, temporal, and noise components

**Data flow**: Raw records → Extractors → Feature vectors → Profile Layer

**Key algorithms**: ALG-001 (Feature Extraction), ALG-002 (Signal Extraction), ALG-005 (Signal Decomposition)

#### Profile Layer

Assembles feature vectors into structured behavioral profiles and estimates Cognitive Centroids.

**Components**:
- **PF-001**: Profile Constructor — Aggregates feature vectors by individual and modality
- **PF-002**: Profile Normalizer — Cross-context normalization (ALG-008)
- **PF-003**: Centroid Estimator — Cognitive Centroid estimation (ALG-009)
- **PF-004**: Profile Aggregator — Multi-session profile combination (ALG-011)

**Data flow**: Feature vectors → Profile Constructor → Normalizer → Centroid Estimator → Comparison Layer

**Key algorithms**: ALG-006, ALG-008, ALG-009, ALG-011
**Key metrics**: Convergence slope (AC-002E), normalization correctness (AC-002F)

#### Comparison Layer

Matches questioned profiles against reference profiles to produce similarity scores.

**Components**:
- **CP-001**: Behavior Comparator — Profile-to-profile comparison (ALG-007)
- **CP-002**: Identity Matcher — 1:N database search (ALG-010)
- **CP-003**: Identity Verifier — 1:1 verification (ALG-012)
- **CP-004**: Similarity Engine — Five similarity functions (ALG-024 — ALG-028)

**Data flow**: Profiles → Comparator → Similarity scores → Evidence Layer

**Key algorithms**: ALG-007, ALG-010, ALG-024 — ALG-028
**Key metrics**: AUC (AC-003A), d-prime (AC-003I), Rank-1 (AC-003G)

#### Evidence Layer

Transforms similarity scores into weighted likelihood ratios and fuses across modalities.

**Components**:
- **EV-001**: Evidence Accumulator — Temporal evidence aggregation (ALG-013)
- **EV-002**: Evidence Weighter — Quality, relevance, recency weighting (ALG-014)
- **EV-003**: LR Calibrator — Score-to-LR calibration (ALG-017)
- **EV-004**: Fusion Engine — Multi-modal evidence combination (ALG-029, ALG-030, ALG-031, ALG-032)
- **EV-005**: Confidence Estimator — Attribution confidence (ALG-019, ALG-020)

**Data flow**: Similarity scores → Calibrator → LRs → Fusion Engine → Combined LR → Decision Layer

**Key algorithms**: ALG-013 — ALG-020
**Key metrics**: Cllr (AC-003F), ECE (AC-003E), fusion improvement (AC-002H)

#### Decision Layer

Produces final attribution conclusions with quantified uncertainty.

**Components**:
- **DC-001**: Threshold Decider — Applies decision thresholds (ALG-033)
- **DC-002**: Threshold Optimizer — Operational threshold optimization (ALG-034)
- **DC-003**: Quality Rejecter — FTE/FTX rejection (ALG-035)
- **DC-004**: Sequential Decider — Sequential evidence accumulation (ALG-036)
- **DC-005**: Adaptive Threshold — Dynamic threshold adjustment (ALG-041)

**Data flow**: Combined LR → Threshold comparison → Attribution conclusion

**Key algorithms**: ALG-033 — ALG-036, ALG-041
**Key metrics**: FAR (AC-003C), FRR (AC-003D), EER (AC-003B)

---

## 3. Six-Stage Pipeline

### 3.1 Pipeline Data Flow

```
┌──────────┐   ┌──────────┐   ┌──────────┐   ┌──────────┐   ┌──────────┐   ┌──────────┐
│  EXTRACT │ → │ CONSTRUCT│ → │ COMPARE  │ → │CALIBRATE │ → │  FUSE    │ → │  DECIDE  │
│  Stage 1 │   │  Stage 2 │   │  Stage 3 │   │  Stage 4 │   │  Stage 5 │   │  Stage 6 │
└──────────┘   └──────────┘   └──────────┘   └──────────┘   └──────────┘   └──────────┘
      │              │              │              │              │              │
      ▼              ▼              ▼              ▼              ▼              ▼
 Feature        Behavioral      Similarity    Likelihood     Combined       Attribution
 Vectors        Profiles         Scores        Ratios           LR         Conclusion
```

### 3.2 Stage Details

| Stage | Layer | Input | Processing | Output |
|---|---|---|---|---|
| 1. Extract | Data + Feature | Raw data | Feature extraction, signal decomposition | Feature vectors |
| 2. Construct | Profile | Feature vectors | Aggregation, normalization, centroid estimation | Behavioral profiles |
| 3. Compare | Comparison | Profiles | Similarity computation, ranking | Similarity scores |
| 4. Calibrate | Evidence | Scores | Score distribution modeling, LR computation | Likelihood ratios |
| 5. Fuse | Evidence | LRs | Weighting, multi-modal fusion | Combined LR |
| 6. Decide | Decision | Combined LR | Threshold comparison, quality check | Attribution conclusion |

---

## 4. Three Workflows

### 4.1 Workflow Configurations

| Aspect | Identification | Verification | Forensic Comparison |
|---|---|---|---|
| **Question** | Who is this? | Is this who they claim? | What is the evidence strength? |
| **Match type** | 1:N | 1:1 | 1:1 with LR |
| **Database required** | Yes | Optional (reference profile) | Yes (background population) |
| **Primary metric** | Rank-1 accuracy | FAR, FRR | Cllr |
| **Decision output** | Identity label | Accept/Reject | LR + confidence |
| **Inconclusive allowed** | Yes (not found) | Yes (insufficient) | Yes (LR near 1) |

### 4.2 Identification Workflow

```
Input: Questioned behavioral data
  ↓
1. Extract features (all available modalities)
2. Construct questioned profile
3. Compare against N reference profiles in database
4. Rank by similarity score
5. If top score > tau_id:
     Return matched identity
   Else:
     Return "not in database"
  ↓
Output: Identity or "not found"
```

### 4.3 Verification Workflow

```
Input: Questioned data + claimed identity
  ↓
1. Extract features from questioned data
2. Construct questioned profile
3. Retrieve reference profile for claimed identity
4. Compute similarity score
5. Calibrate similarity to LR
6. If LR > tau_vrf:
     Accept claimed identity
   Else if LR < 1/tau_vrf:
     Reject claimed identity
   Else:
     Inconclusive
  ↓
Output: Accept/Reject/Inconclusive
```

### 4.4 Forensic Comparison Workflow

```
Input: Questioned data + suspect reference profile
  ↓
1. Extract features from all available modalities
2. Construct questioned profile per modality
3. Compare each modality against suspect reference
4. Compute modality-specific LRs
5. Weight LRs by quality, relevance, recency
6. Fuse LRs using selected fusion strategy
7. Compute combined LR with confidence intervals
8. Apply forensic threshold:
     LR > tau_for: Positive attribution
     LR < 1/tau_for: Exclusion
     Otherwise: Inconclusive
  ↓
Output: Forensic report with LR, ACM, and uncertainty bounds
```

---

## 5. Five Behavioral Modalities

### 5.1 Modality Architecture

Each modality follows an identical architectural pattern:

```
Modality Data → Extractor → Feature Vector → Profile Constructor → Behavioral Profile
                                                              ↓
                                                     Similarity Function → Score
```

### 5.2 Modality Specifications

#### Stylometry (SM-001)

| Aspect | Specification |
|---|---|
| Data source | Text content (tweets, posts, messages) |
| Feature groups | Function-word frequencies, syntactic patterns, lexical diversity |
| Feature dimension | 100+ (varies by implementation) |
| Embedding models | MarBERT, AraBERT, MPNet (ensemble) |
| Similarity metric | Cosine (ALG-024) |
| Involuntariness | HIGH (function words) |
| Prototype status | IMPLEMENTED (372-dim fingerprint) |

#### Chrono-Profiling (CP-001)

| Aspect | Specification |
|---|---|
| Data source | Timestamped activity records |
| Feature groups | Circadian rhythms, inter-event intervals, periodicity |
| Feature dimension | 50+ |
| Key measures | Burstiness, hour entropy, weekday entropy, avg interpost time |
| Similarity metric | Pearson correlation (ALG-027) |
| Involuntariness | HIGH |
| Prototype status | NOT IMPLEMENTED (no timestamps) |

#### Terminal Profiling (TP-001)

| Aspect | Specification |
|---|---|
| Data source | Command logs, interaction records |
| Feature groups | Command sequences, timing patterns, error patterns |
| Feature dimension | 80+ |
| Key measures | Sequence edit distance, timing rhythms, tool preferences |
| Similarity metric | RBF (ALG-026) |
| Involuntariness | VERY HIGH |
| Prototype status | NOT IMPLEMENTED |

#### Network Analysis (NA-001)

| Aspect | Specification |
|---|---|
| Data source | Social graph, interaction networks |
| Feature groups | Topology, centrality, community structure |
| Feature dimension | 60+ |
| Key measures | Degree, betweenness, eigenvector centrality |
| Similarity metric | Jaccard (ALG-028) |
| Involuntariness | MEDIUM |
| Prototype status | PARTIAL (graph engine exists, untested) |

#### Media Forensics (MF-001)

| Aspect | Specification |
|---|---|
| Data source | File metadata, environment artifacts |
| Feature groups | Naming conventions, organizational structure, tool preferences |
| Feature dimension | 40+ |
| Key measures | Directory depth, naming patterns, metadata consistency |
| Similarity metric | Cosine (ALG-024) |
| Involuntariness | HIGH |
| Prototype status | NOT IMPLEMENTED |

---

## 6. Fusion Architecture

### 6.1 Fusion Framework

```
                ┌──────────────────────┐
                │  Modality 1 (LR_1)   │
                │  Modality 2 (LR_2)   │
Evidence LRs →  │  Modality 3 (LR_3)   │ → Fusion → Combined LR → Decision
                │  Modality 4 (LR_4)   │
                │  Modality 5 (LR_5)   │
                └──────────────────────┘
```

### 6.2 Fusion Strategies

#### Score-Level Fusion (ALG-030)

```
s_fused = sum(w_m * s_m)  where s_m are modality similarity scores
LR_combined = calibrate(s_fused)
```

#### Feature-Level Fusion (ALG-031)

```
f_fused = HOSVD([f_1, f_2, ..., f_M])  -- tensor factorization
profile_fused = construct_profile(f_fused)
s = compare(profile_fused, reference_fused)
LR_combined = calibrate(s)
```

#### Decision-Level Fusion (ALG-032)

```
LR_m = calibrate(s_m) for each modality
LR_combined = product(LR_m ^ w_m)
```

---

## 7. Decision Framework

### 7.1 Decision Parameters

| Parameter | Symbol | Purpose | Applied In |
|---|---|---|---|
| Identification threshold | tau_id | Minimum similarity for identity match | ALG-033 |
| Verification LR threshold | tau_vrf | Minimum LR for verification accept | ALG-033 |
| Forensic LR threshold | tau_for | Minimum LR for positive attribution | ALG-033 |
| Inconclusive upper bound | tau_inc_u | Upper bound of inconclusive zone | ALG-033 |
| Inconclusive lower bound | tau_inc_l | Lower bound of inconclusive zone | ALG-033 |
| FTE quality threshold | Q_FTE | Minimum quality for enrollment | ALG-035 |
| FTX quality threshold | Q_FTX | Minimum quality for extraction | ALG-035 |
| Cost ratio (FAR:FRR) | C_ratio | Relative cost of errors | ALG-034 |

### 7.2 Decision Logic

```
if quality < Q_FTX:
    output = FailureToExtract
elif modalities_available < min_modalities:
    output = Inconclusive (insufficient modalities)
else:
    combined_lr = fuse(modality_lrs)
    if combined_lr > tau_for:
        output = PositiveAttribution(combined_lr, confidence)
    elif combined_lr < 1/tau_for:
        output = Exclusion(combined_lr, confidence)
    else:
        output = Inconclusive(combined_lr, confidence)
```

---

## 8. Component Catalog

| ID | Component | Layer | Algorithm(s) | Status |
|---|---|---|---|---|
| DT-001 | Data Acquisition Interface | Data | — | PARTIAL |
| DT-002 | Data Validator | Data | ALG-035 | DEFINED |
| DT-003 | Data Store | Data | — | WORKING |
| DT-004 | Index Store | Data | ALG-010 | VERIFIED |
| FT-001 | Stylometric Extractor | Feature | ALG-001, ALG-002 | IMPLEMENTED |
| FT-002 | Chrono Extractor | Feature | ALG-001, ALG-002 | NOT IMPLEMENTED |
| FT-003 | Terminal Extractor | Feature | ALG-001, ALG-002 | NOT IMPLEMENTED |
| FT-004 | Network Extractor | Feature | ALG-001, ALG-002 | PARTIAL |
| FT-005 | Media Extractor | Feature | ALG-001, ALG-002 | NOT IMPLEMENTED |
| FT-006 | Signal Decomposer | Feature | ALG-005 | DEFINED |
| PF-001 | Profile Constructor | Profile | ALG-006 | IMPLEMENTED |
| PF-002 | Profile Normalizer | Profile | ALG-008 | DEFINED |
| PF-003 | Centroid Estimator | Profile | ALG-009 | DEFINED |
| PF-004 | Profile Aggregator | Profile | ALG-011 | DEFINED |
| CP-001 | Behavior Comparator | Comparison | ALG-007 | IMPLEMENTED |
| CP-002 | Identity Matcher | Comparison | ALG-010 | VERIFIED |
| CP-003 | Identity Verifier | Comparison | ALG-012 | TBD |
| CP-004 | Similarity Engine | Comparison | ALG-024 — ALG-028 | VERIFIED |
| EV-001 | Evidence Accumulator | Evidence | ALG-013 | DEFINED |
| EV-002 | Evidence Weighter | Evidence | ALG-014 | DEFINED |
| EV-003 | LR Calibrator | Evidence | ALG-017 | DEFINED |
| EV-004 | Fusion Engine | Evidence | ALG-029 — ALG-032 | DEFINED |
| EV-005 | Confidence Estimator | Evidence | ALG-019, ALG-020 | DEFINED |
| DC-001 | Threshold Decider | Decision | ALG-033 | DEFINED |
| DC-002 | Threshold Optimizer | Decision | ALG-034 | DEFINED |
| DC-003 | Quality Rejecter | Decision | ALG-035 | DEFINED |
| DC-004 | Sequential Decider | Decision | ALG-036 | DEFINED |
| DC-005 | Adaptive Threshold | Decision | ALG-041 | FUTURE |

---

## 9. API Interfaces

### 9.1 Processing API

```
POST /extract          — Extract features from raw data
POST /construct        — Build profile from features
POST /compare          — Compare two profiles
POST /calibrate        — Calibrate score to LR
POST /fuse             — Fuse multi-modal evidence
POST /decide           — Make attribution decision
```

### 9.2 Workflow API

```
POST /identify         — 1:N identification
POST /verify           — 1:1 verification
POST /forensic-compare — Forensic comparison
```

### 9.3 Management API

```
GET  /profiles/{id}    — Get profile
PUT  /profiles/{id}    — Update profile
DEL  /profiles/{id}    — Delete profile
POST /index/build      — Build search index
GET  /system/health    — System health check
GET  /system/metrics   — Performance metrics
```

---

## 10. Prototype Architecture (Anubis Twitter v2.5)

### 10.1 Implemented Components

The prototype implements the stylometric modality only:

| Component | Implementation | File |
|---|---|---|
| Data Acquisition | Twitter scraper (Selenium) | scrapers/twitter_scraper_loggedin.py |
| Data Store | SQLite (twitter_egypt.db) | pipeline.py, db_init.py |
| Stylometric Extractor | 3-model ensemble (MarBERT, AraBERT, MPNet) | shared/stylometry_core.py |
| Profile Constructor | 372-dim vector builder | shared/stylometry_core.py |
| Behavior Comparator | Cosine similarity | shared/stylometry_core.py |
| Identity Matcher | FAISS IndexFlatIP | vector/pipeline.py |
| Egyptian Verifier | 3-layer demographic filter | shared/egyptian_verifier.py |
| Dashboard | Django UI with 10 views | UI/anubis_x/core/views.py |

### 10.2 Prototype Data Flow

```
Twitter/X API/Scraper
    ↓ (raw JSON)
Data Validator (quality checks)
    ↓ (validated records)
Feature Extractor (text → features)
    ↓ (feature vectors)
Profile Constructor (build_user_vector)
    ↓ (372-dim fingerprint)
FAISS Index (IndexFlatIP)
    ↓ (similarity search)
Results (ranked matches)
```

### 10.3 Prototype Limitations vs. Full Framework

| Aspect | Prototype | Full Framework |
|---|---|---|
| Modalities | 1 (stylometry) | 5 |
| Fusion | None (single modality) | 3 strategies (score, feature, decision) |
| Workflows | Identification only | Identification, Verification, Forensic |
| Temporal features | Invalid (no timestamps) | Chrono-profiling (50+ features) |
| Network features | Not collected | Relational network analysis |
| Validation | Partial (15/38 experiments) | Full 4-tier hierarchy |
| Accuracy metrics | 7 of 13 computable | All 13 |
| Acceptance criteria | Untested | 33 criteria |
| Database | 31 users | N/A (full framework) |

---

## 11. Relationship to Full Framework

The Architecture described here is the **target architecture** for the complete AnubisX Framework. The Anubis Twitter Intelligence v2.5 prototype implements a subset of this architecture — specifically the Data, Feature, Profile, and Comparison layers for the stylometric modality only.

As the framework matures, additional modalities will be integrated, fusion strategies implemented, and the validation framework populated with empirical results.

---

## 12. Cross-References

| Document | Description | Path |
|---|---|---|
| Overview | Framework overview | [Overview.md](Overview.md) |
| Framework Guide | Implementation guide | [Framework_Guide.md](Framework_Guide.md) |
| Algorithms | Algorithm catalog | [Algorithms.md](Algorithms.md) |
| Validation | Validation methodology | [Validation.md](Validation.md) |
| Multi-Modal Framework | Five modalities and fusion | [Multi_Modal_Framework.md](Multi_Modal_Framework.md) |
| Attribution Framework | LR-based attribution | [Attribution_Framework.md](Attribution_Framework.md) |
| Benchmarking Guide | Evaluation protocols | [Benchmarking_Guide.md](Benchmarking_Guide.md) |

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
