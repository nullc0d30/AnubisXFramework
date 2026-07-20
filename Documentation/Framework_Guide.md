# Framework Guide

**AnubisX Framework v2.0 — Implementation and Integration Guide**

---

## Official DOI

DOI: [10.5281/zenodo.21446923](https://doi.org/10.5281/zenodo.21446923)

This release is permanently archived on Zenodo under DOI: [https://doi.org/10.5281/zenodo.21446923](https://doi.org/10.5281/zenodo.21446923)

---

## 1. Introduction

This guide provides a comprehensive walkthrough of the AnubisX Framework architecture, pipeline, workflows, fusion strategies, decision framework, configuration parameters, and API interfaces. It is intended for engineers and researchers implementing or integrating the framework.

---

## 2. The Six-Layer Architecture

The framework is organized into six layers, each responsible for a distinct phase of the attribution process:

```
┌─────────────────────────────────────────────────────┐
│                   DECISION LAYER                     │
│    Attribution conclusions, LR, ACM, inconclusive    │
├─────────────────────────────────────────────────────┤
│                  EVIDENCE LAYER                      │
│    Fusion, weighting, calibration, LR computation    │
├─────────────────────────────────────────────────────┤
│                 COMPARISON LAYER                     │
│    Profile matching, similarity scoring, ranking     │
├─────────────────────────────────────────────────────┤
│                  PROFILE LAYER                       │
│    Profile construction, normalization, centroid     │
├─────────────────────────────────────────────────────┤
│                  FEATURE LAYER                       │
│    Feature extraction, signal decomposition          │
├─────────────────────────────────────────────────────┤
│                   DATA LAYER                         │
│    Acquisition, validation, storage, preprocessing   │
└─────────────────────────────────────────────────────┘
```

### 2.1 Data Layer

| Component | Function | Key Algorithms |
|---|---|---|
| Data Acquisition | Raw data collection from platforms | Platform-specific scrapers |
| Data Validation | Quality checks, schema validation | FUNC-046, FUNC-047 |
| Data Storage | Structured persistence | SQLite, FAISS indexes |
| Preprocessing | Cleaning, normalization | Text cleaning, Arabic normalization |

**Inputs**: Raw platform data (tweets, posts, interactions)
**Outputs**: Validated, cleaned data records
**Key constraints**: P3 Protocol proportionality, minimum data quality thresholds

### 2.2 Feature Layer

| Component | Function | Key Algorithms |
|---|---|---|
| Feature Extraction | Transform raw data to feature vectors | ALG-001 |
| Signal Extraction | Isolate behavioral signals from raw features | ALG-002 |
| Evidence Extraction | Extract evidence from signals | ALG-003 |
| Signal Decomposition | Separate cognitive signal from confounds | ALG-005 |

**Inputs**: Cleaned data records
**Outputs**: Modality-specific feature vectors
**Key constraints**: Feature dimension consistency, numerical stability (AC-001D)

### 2.3 Profile Layer

| Component | Function | Key Algorithms |
|---|---|---|
| Profile Construction | Assemble feature vectors into profiles | ALG-006 |
| Profile Normalization | Normalize across contexts and time | ALG-008 |
| Centroid Estimation | Estimate Cognitive Centroid | ALG-009 |
| Profile Aggregation | Combine multi-session profiles | ALG-011 |

**Inputs**: Feature vectors
**Outputs**: Behavioral profiles with Cognitive Centroid estimates
**Key constraints**: Convergence (AC-002A, AC-002E), normalization correctness (AC-002F)

### 2.4 Comparison Layer

| Component | Function | Key Algorithms |
|---|---|---|
| Behavior Comparison | Compare questioned vs. reference profiles | ALG-007 |
| Identity Matching | Match against database of known profiles | ALG-010 |
| Identity Verification | Verify claimed identity (1:1) | ALG-012 |
| Similarity Computation | Compute similarity scores | ALG-024 — ALG-028 |

**Inputs**: Behavioral profiles
**Outputs**: Similarity scores
**Key constraints**: Metric axioms (AC-002G), symmetry (AC-001F)

### 2.5 Evidence Layer

| Component | Function | Key Algorithms |
|---|---|---|
| Evidence Accumulation | Aggregate evidence over time | ALG-013 |
| Evidence Weighting | Weight by quality, relevance, recency | ALG-014 |
| Evidence Fusion | Combine multi-modal evidence | ALG-015 |
| Temporal Integration | Integrate temporal evidence | ALG-016 |
| LR Computation | Compute Likelihood Ratio | ALG-017 |
| Multi-Modal Attribution | Combine modality LRs | ALG-018 |
| Confidence Estimation | Estimate attribution confidence | ALG-019, ALG-020 |

**Inputs**: Similarity scores
**Outputs**: Weighted LRs, confidence estimates
**Key constraints**: Fusion improvement (AC-002H), LR cost (AC-003F)

### 2.6 Decision Layer

| Component | Function | Key Algorithms |
|---|---|---|
| Threshold Decision | Apply decision threshold | ALG-033 |
| Threshold Optimization | Optimize operational threshold | ALG-034 |
| FTE/FTX Rejection | Quality-based rejection | ALG-035 |
| Sequential Decision | Sequential evidence accumulation | ALG-036 |
| Adaptive Threshold | Dynamic threshold adjustment | ALG-041 |

**Inputs**: Combined LR, confidence estimates
**Outputs**: Attribution conclusion (identification, verification, inconclusive)
**Key constraints**: FAR <= 0.001 at FRR = 0.01 (AC-003C), EER <= 0.08 (AC-003B)

---

## 3. The Six-Stage Pipeline

The pipeline processes data through six sequential stages:

```
[Stage 1]     [Stage 2]     [Stage 3]     [Stage 4]     [Stage 5]     [Stage 6]
  EXTRACT  →   CONSTRUCT →   COMPARE   →   CALIBRATE →    FUSE     →   DECIDE
    │             │             │             │             │             │
    ▼             ▼             ▼             ▼             ▼             ▼
Feature       Profile      Similarity    Likelihood    Combined      Attribution
 Vectors       Profiles      Scores        Ratios          LR        Conclusion
```

### Stage 1: Extract

Modality-specific extractors process raw data:
- **Stylometry**: Text → function-word frequencies, syntax patterns, lexical features
- **Chrono-Profiling**: Timestamps → circadian patterns, inter-event intervals
- **Terminal Profiling**: Interaction logs → command sequences, timing rhythms
- **Network Analysis**: Social graph → topology metrics, interaction frequencies
- **Media Forensics**: File metadata → organizational patterns

**Output**: Feature vectors (one per modality per observation)

### Stage 2: Construct

Feature vectors are assembled into behavioral profiles:
1. Aggregate feature vectors by individual and modality
2. Estimate Cognitive Centroid per modality (ALG-009)
3. Normalize profiles (ALG-008)
4. Assign confidence based on observation count

**Output**: Multi-modal behavioral profiles with centroid estimates

### Stage 3: Compare

Questioned profiles are compared against reference profiles:
1. Select appropriate similarity measure (ALG-024 — ALG-028)
2. Compute similarity score per modality
3. For identification: 1:N search; for verification: 1:1 match

**Output**: Similarity scores per modality

### Stage 4: Calibrate

Similarity scores are transformed into likelihood ratios:
1. Estimate score distributions for same-source and different-source pairs
2. Apply calibration function (ALG-017)
3. Compute LR with confidence intervals

**Output**: Calibrated LRs per modality

### Stage 5: Fuse

Multi-modal LRs are fused into a combined LR:
1. Weight each modality by quality, relevance, recency (ALG-014)
2. Apply fusion strategy (score-level, feature-level, or decision-level)
3. Compute combined LR (ALG-018)
4. Estimate attribution confidence (ALG-019, ALG-020)

**Output**: Combined LR with confidence estimate

### Stage 6: Decide

The combined LR supports an attribution decision:
1. Compare LR against decision thresholds (ALG-033)
2. Apply FTE/FTX rejection if quality insufficient (ALG-035)
3. For sequential evidence: update decision as evidence accumulates (ALG-036)
4. Output conclusion with quantified uncertainty

**Output**: Attribution conclusion (identify, verify, inconclusive)

---

## 4. The Five Behavioral Modalities

### 4.1 Modality Specifications

| Modality | Data Source | Features | Feature Count | Comparison Method |
|---|---|---|---|---|
| Forensic Stylometry | Text content | Function words, syntax, vocabulary, readability | 100+ | Cosine similarity (ALG-024) |
| Chrono-Profiling | Timestamps | Circadian rhythms, inter-event timing, periodicity | 50+ | Pearson correlation (ALG-027) |
| Terminal Profiling | Interaction logs | Command sequences, timing, error patterns | 80+ | RBF similarity (ALG-026) |
| Network Analysis | Social graph | Topology, centrality, community structure | 60+ | Jaccard similarity (ALG-028) |
| Media Forensics | File metadata | Organization, naming, tool preferences | 40+ | Cosine similarity (ALG-024) |

### 4.2 Modality Contributions

| Modality | Discriminability | Robustness | Involuntariness | Implementation Status |
|---|---|---|---|---|
| Stylometry | HIGH | MEDIUM | HIGH | IMPLEMENTED |
| Chrono-Profiling | MEDIUM | LOW | HIGH | NOT IMPLEMENTED |
| Terminal Profiling | HIGH | HIGH | VERY HIGH | NOT IMPLEMENTED |
| Network Analysis | MEDIUM | MEDIUM | MEDIUM | NOT IMPLEMENTED |
| Media Forensics | LOW | HIGH | HIGH | NOT IMPLEMENTED |

---

## 5. Three Primary Workflows

### 5.1 Identification (1:N)

**Purpose**: Determine which known individual produced the questioned behavior.
**Use case**: Unknown actor attribution against a database of known profiles.

```
Questioned behavior → Feature extraction → Profile construction
    → Compare against N reference profiles → Rank by similarity
    → Apply threshold → Top match or "not in database"
```

**Key algorithms**: ALG-010 (Identity Matching), ALG-033 (Threshold Decision)
**Key metrics**: Rank-1 accuracy (AC-003G), AUC (AC-003A)

### 5.2 Verification (1:1)

**Purpose**: Verify whether the questioned behavior matches a claimed identity.
**Use case**: Access control, login verification, identity confirmation.

```
Questioned behavior → Feature extraction → Profile construction
    → Compare against claimed reference profile → Similarity score
    → Calibrate to LR → Compare against verification threshold
    → Accept or reject claimed identity
```

**Key algorithms**: ALG-012 (Identity Verification), ALG-017 (LR Computation)
**Key metrics**: FAR (AC-003C), FRR (AC-003D), EER (AC-003B)

### 5.3 Forensic Comparison

**Purpose**: Quantify the strength of evidence linking questioned behavior to a suspect.
**Use case**: Legal proceedings, internal investigations, intelligence analysis.

```
Questioned behavior → Feature extraction → Profile construction
    → Compare against suspect's reference profile → Similarity score
    → Calibrate to LR → Weight and fuse across modalities
    → Report LR with uncertainty bounds → Inconclusive if insufficient
```

**Key algorithms**: ALG-017 (LR Computation), ALG-018 (Multi-Modal Attribution), ALG-014 (Evidence Weighting)
**Key metrics**: Cllr (AC-003F), ECE (AC-003E)

---

## 6. Multi-Modal Fusion Strategies

### 6.1 Score-Level Fusion (ALG-030)

Combines similarity scores before LR transformation.

```
s_fused = sum(w_m * s_m)
LR = calibrate(s_fused)
```

**Advantages**: Simplest implementation, most robust to missing data
**Disadvantages**: Loses modality-specific calibration information
**Best for**: Prototypes, early deployment, balanced modalities

### 6.2 Feature-Level Fusion (ALG-031)

Concatenates feature vectors before profile construction.

```
f_fused = [f_1, f_2, ..., f_M]  via HOSVD
profile = construct_profile(f_fused)
```

**Advantages**: Captures cross-modal interactions, potentially highest accuracy
**Disadvantages**: High dimensionality, requires complete data, computationally intensive
**Best for**: Research, high-accuracy requirements

### 6.3 Decision-Level Fusion (ALG-032)

Combines independent modality decisions.

```
LR_combined = product(LR_m ^ w_m)
decision = threshold(LR_combined)
```

**Advantages**: Preserves modality independence, supports missing modalities
**Disadvantages**: Does not capture cross-modal interactions
**Best for**: Heterogeneous data availability, operational deployment

### 6.4 Fusion Comparison

| Criterion | Score-Level | Feature-Level | Decision-Level |
|---|---|---|---|
| Implementation complexity | LOW | HIGH | MEDIUM |
| Accuracy potential | MEDIUM | HIGH | MEDIUM |
| Missing data handling | GOOD | POOR | GOOD |
| Cross-modal interaction | NO | YES | NO |
| Computational cost | LOW | HIGH | LOW |
| Interpretability | HIGH | LOW | HIGH |

---

## 7. Decision Framework

### 7.1 Likelihood Ratio

The central decision quantity:

```
LR = P(E | H_p) / P(E | H_d)
```

### 7.2 Decision Thresholds

| Threshold | Symbol | Purpose | Typical Value |
|---|---|---|---|
| Identification threshold | tau_id | Minimum similarity for ID match | TBD by calibration |
| Verification threshold | tau_vrf | Minimum LR for verification | LR = 100 |
| Forensic threshold | tau_for | Minimum LR for positive attribution | LR = 1000 |
| Inconclusive upper bound | tau_inc_upper | Below this, inconclusive | LR = 10 |
| Inconclusive lower bound | tau_inc_lower | Above this, inconclusive | LR = 0.1 |
| FTE threshold | Q_FTE | Minimum quality for enrollment | TBD |
| FTX threshold | Q_FTX | Minimum quality for extraction | TBD |

### 7.3 Attribution Confidence Metric (ACM)

The ACM quantifies the reliability of each attribution decision:

```
ACM = f(confidence, evidence_quantity, modality_count, LR_stability)
```

Components:
- **Confidence (ALG-020)**: Within-class distance relative to between-class distance
- **Evidence quantity**: Number of observations supporting the conclusion
- **Modality count**: Number of modalities contributing evidence
- **LR stability**: Variance of LR estimate across bootstrap samples

### 7.4 Inconclusive Determination

Per DP-ATR-004, inconclusive outcomes are valid and must be clearly distinguished from negative outcomes:

| Condition | Conclusion |
|---|---|
| LR > tau_for | Positive attribution |
| LR < 1/tau_for | Negative attribution (exclusion) |
| 1/tau_for <= LR <= tau_for | Inconclusive |
| Insufficient evidence | Inconclusive |
| Quality below threshold | Inconclusive (FTE/FTX) |

---

## 8. Configuration Parameters

### 8.1 Global Parameters

| Parameter | Type | Default | Description |
|---|---|---|---|
| min_modalities | int | 2 | Minimum modalities required for attribution (DP-ATR-001) |
| min_observations | int | 10 | Minimum observations per modality per individual |
| quality_threshold | float | 0.5 | Minimum quality score for data acceptance |
| temporal_decay_constant | float | 0.95 | Evidence weight decay per time unit |
| confidence_alpha | float | 0.05 | Significance level for confidence intervals |

### 8.2 Modality-Specific Parameters

| Parameter | Stylometry | Chrono | Terminal | Network | Media |
|---|---|---|---|---|---|
| embedding_dim | 256 | — | — | — | — |
| n_lexical_features | 16 | — | — | — | — |
| n_topic_features | 100 | — | — | — | — |
| n_temporal_features | — | 8 | — | — | — |
| n_sequence_features | — | — | 12 | — | — |
| n_topology_features | — | — | — | 10 | — |
| n_environment_features | — | — | — | — | 8 |
| similarity_measure | COSINE | PEARSON | RBF | JACCARD | COSINE |

### 8.3 Fusion Parameters

| Parameter | Type | Default | Description |
|---|---|---|---|
| fusion_strategy | enum | SCORE_LEVEL | Fusion strategy (SCORE/FEATURE/DECISION) |
| modality_weights | float[5] | [0.3, 0.2, 0.2, 0.15, 0.15] | Modality importance weights |
| quality_weight | float | 1.0 | Evidence quality weight exponent |
| relevance_weight | float | 1.0 | Evidence relevance weight exponent |
| recency_weight | float | 0.5 | Evidence recency weight exponent |

### 8.4 Decision Parameters

| Parameter | Type | Default | Description |
|---|---|---|---|
| tau_identification | float | 0.85 | Identification similarity threshold |
| tau_verification | float | 100.0 | Verification LR threshold |
| tau_forensic | float | 1000.0 | Forensic LR threshold |
| tau_inconclusive_upper | float | 10.0 | Inconclusive upper LR bound |
| tau_inconclusive_lower | float | 0.1 | Inconclusive lower LR bound |
| cost_ratio | float | 10.0 | C_FAR / C_FRR cost ratio |

---

## 9. API Interfaces (Conceptual)

### 9.1 Core API

```python
# Feature Extraction
feature_vector = extract_features(data: RawData, modality: Modality) -> FeatureVector

# Profile Construction
profile = construct_profile(features: List[FeatureVector]) -> BehavioralProfile

# Profile Comparison
similarity = compare_profiles(query: BehavioralProfile, reference: BehavioralProfile) -> float

# Evidence Calibration
lr = calibrate_to_lr(similarity: float, modality: Modality) -> LikelihoodRatio

# Multi-Modal Fusion
combined_lr = fuse_evidence(lrs: List[WeightedLR], strategy: FusionStrategy) -> LikelihoodRatio

# Decision
decision = decide(combined_lr: LikelihoodRatio, context: DecisionContext) -> AttributionConclusion
```

### 9.2 Workflow APIs

```python
# Identification (1:N)
result = identify(
    questioned_data: RawData,
    database: ProfileDatabase,
    threshold: float = 0.85
) -> IdentificationResult

# Verification (1:1)
result = verify(
    questioned_data: RawData,
    claimed_identity: IdentityClaim,
    threshold: float = 100.0
) -> VerificationResult

# Forensic Comparison
result = forensic_compare(
    questioned_data: RawData,
    suspect_profile: BehavioralProfile,
    context: ForensicContext
) -> ForensicReport
```

### 9.3 Management APIs

```python
# Profile Management
profile = create_profile(individual_id: str, modality: Modality)
profile = update_profile(profile_id: str, new_data: RawData)
profile = get_profile(individual_id: str, modality: Modality)

# Database Management
index = build_index(database: ProfileDatabase, algorithm: str = "FlatIP")
stats = get_database_stats(database: ProfileDatabase)

# System Management
health = get_system_health()
metrics = get_performance_metrics()
```

---

## 10. Cross-References

| Document | Description | Path |
|---|---|---|
| Overview | Framework overview | [Overview.md](Overview.md) |
| Architecture | Six-layer architecture | [Architecture.md](Architecture.md) |
| Theory Guide | Theoretical foundations | [Theory_Guide.md](Theory_Guide.md) |
| Algorithms | Algorithm catalog | [Algorithms.md](Algorithms.md) |
| Validation | Validation methodology | [Validation.md](Validation.md) |
| Examples | Code examples | [Examples.md](Examples.md) |
| Axiomatic System | 16 axioms, 20 hypotheses, 18 design principles | [Axiomatic_System.md](Axiomatic_System.md) |
| Attribution Framework | LR-based attribution | [Attribution_Framework.md](Attribution_Framework.md) |
| Multi-Modal Framework | Five modalities and fusion | [Multi_Modal_Framework.md](Multi_Modal_Framework.md) |
| Benchmarking Guide | Evaluation scenarios | [Benchmarking_Guide.md](Benchmarking_Guide.md) |

---

---

**Project**: AnubisX Framework  
**Primary Author**: Ahmed Awad (NullC0d3)  
**Author Profile**: https://www.linkedin.com/in/nullc0d3/  
**ORCID**: https://orcid.org/0009-0005-0654-3393  
**Original Framework**: Ahmed Awad (NullC0d3)  
**Original Research**: Ahmed Awad (NullC0d3)  
**Repository**: [https://github.com/AnubisXFramework/AnubisXFramework](https://github.com/AnubisXFramework/AnubisXFramework)  

**DOI**: [https://doi.org/10.5281/zenodo.21446923](https://doi.org/10.5281/zenodo.21446923)

**Copyright** © 2026 Ahmed Awad (NullC0d3). All rights reserved.  
Original documentation, framework design, algorithms, source code, diagrams, and repository structure are the intellectual work of Ahmed Awad (NullC0d3), unless otherwise indicated. Third-party software, libraries, datasets, and referenced works remain the property of their respective owners and are governed by their own licenses.

---

*Classification: PUBLIC (C0)*
*Version: 1.0*


