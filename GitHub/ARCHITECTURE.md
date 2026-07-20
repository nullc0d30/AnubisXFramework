# Architecture

**AnubisX Framework — System Architecture Overview**

**Source**: Framework/Framework_Architecture.md (FWK-001), Framework/Framework_Pipeline.md (FWK-004), Documentation/Architecture.md

---

## Architectural Overview

The AnubisX Framework defines a layered, modular architecture for behavioral identity attribution. The architecture separates concerns across six layers, each with well-defined interfaces and responsibilities.

### Six-Layer Architecture

```
┌──────────────────────────────────────────────────────────────────────┐
│                    Decision Layer                          [PARTIAL] │
│  Threshold comparison, attribution/exclusion/inconc                  │
├──────────────────────────────────────────────────────────────────────┤
│                   Evidence Layer                          [PARTIAL] │
│  Calibration, weighting, fusion, confidence estimation               │
├──────────────────────────────────────────────────────────────────────┤
│                  Comparison Layer                         [VALIDATED]│
│  Similarity functions, distance metrics, scoring                     │
├──────────────────────────────────────────────────────────────────────┤
│                  Profile Layer                           [VALIDATED]│
│  Profile construction, storage, versioning, updates                  │
├──────────────────────────────────────────────────────────────────────┤
│                  Feature Layer                          [VALIDATED] │
│  Feature extraction, normalization, transformation                   │
├──────────────────────────────────────────────────────────────────────┤
│                    Data Layer                            [VALIDATED]│
│  Ingestion, validation, metadata extraction, storage                 │
└──────────────────────────────────────────────────────────────────────┘
```

### Architectural Principles

| Principle | Description |
|---|---|
| **Modularity** | Each layer and modality is independently replaceable |
| **Standardization** | All layers use standardized data formats defined in Mathematics/Data_Type_Definitions.md |
| **Composability** | Stages can be flexibly composed — any subset of modalities and fusion strategies |
| **Auditability** | Every processing step is recorded for full traceability |
| **Uncertainty Propagation** | All layers propagate uncertainty estimates through the pipeline |

**Source**: Framework/Framework_Architecture.md (FWK-001) §1.2

---

## Six-Stage Pipeline

### Stage 1: Data Ingestion

```
Raw Data → Format Validation → Metadata Extraction → Storage
```

Platform adapters normalize input from different sources. Chain-of-custody metadata is established. **Source**: Framework/Framework_Pipeline.md (FWK-004) §Stage 1

### Stage 2: Feature Extraction

```
Stored Data → Modality Routing → Feature Computation → Normalization → Feature Vector
```

Five modality-specific extractors (ALG-001—004) run in parallel, transforming raw data into structured feature vectors. Platform and context normalization is applied. **Source**: Algorithms/Core_Algorithms.md (ALG-001—004), Documentation/Architecture.md §2.2

### Stage 3: Profile Construction

```
Feature Vectors → Temporal Aggregation → Profile Assembly → Profile Storage
```

Features are aggregated across observations to build modality-specific behavioral profiles with confidence bounds (ALG-006). Temporal decay accounts for signal degradation (HYP-BEH-003). **Source**: Algorithms/Behavior_Algorithms.md (ALG-006), Algorithms/Evidence_Algorithms.md (ALG-016)

### Stage 4: Comparison

```
Questioned Profile + Reference Profile → Similarity Computation → Score Vector
```

Profiles are compared using five similarity functions (ALG-024—028): Cosine Similarity (EQ-024), Euclidean Distance (EQ-025), RBF Similarity (EQ-026), Pearson Correlation (EQ-027), Jaccard Similarity (EQ-028). **Source**: Algorithms/Similarity_Algorithms.md (ALG-024—028)

### Stage 5: Evidence Evaluation

```
Score Vector → Calibration → Weighting → Fusion → Combined LR
```

Similarity scores are calibrated into Likelihood Ratios (ALG-017, EQ-017), weighted by quality/relevance/recency, and fused across modalities. Three fusion strategies: score-level (ALG-030), feature-level via HOSVD (ALG-031), and decision-level with Dempster-Shafer combination (ALG-032). **Source**: Algorithms/Attribution_Algorithms.md (ALG-017), Algorithms/Fusion_Algorithms.md (ALG-029—032)

### Stage 6: Decision

```
Combined LR → Threshold Comparison → Decision → Report
```

The combined LR is compared against decision thresholds (ALG-033—034). Conclusions: same-source (attribution), different-source (exclusion), or inconclusive. Sequential decision procedures (ALG-036) allow evidence accumulation. Confidence is quantified using the Attribution Confidence Metric (ALG-019—022). **Source**: Algorithms/Decision_Algorithms.md (ALG-033—036)

---

## Three Primary Workflows

| Workflow | Purpose | Output | Source |
|---|---|---|---|
| **Identification** | Determine who produced questioned material | Matched identity or exclusion | Framework/Workflow.md (FWK-002) §2 |
| **Verification** | Confirm or refute a claimed identity | LR for claimed identity | Framework/Workflow.md (FWK-002) §3 |
| **Forensic Comparison** | Compare questioned to reference set | LR for each comparison | Framework/Workflow.md (FWK-002) §4 |

---

## Components

| Component | Layer | Responsibility | Prototype | Source |
|---|---|---|---|---|---|
| Platform Adapter | Data | Normalize platform-specific data formats | ✅ Twitter API adapter validated | Specifications/Component_Specifications.md (SPC-001) |
| Data Validator | Data | Verify input schema and data types | ✅ Data schema validation tested | Specifications/Component_Specifications.md (SPC-001) |
| Modality Router | Feature | Determine which extractors to apply | ✅ Stylometry routing active | Specifications/Component_Specifications.md (SPC-001) |
| Feature Extractor (5) | Feature | Compute behavioral features per modality | ✅ 372-dim stylometric extractor validated | Algorithms/Core_Algorithms.md (ALG-001—004) |
| Feature Normalizer | Feature | Platform and context normalization | ✅ Normalization pipeline tested | Algorithms/Core_Algorithms.md (ALG-008) |
| Profile Builder | Profile | Aggregate features into profiles | ✅ Profile construction validated on 31 accounts | Algorithms/Behavior_Algorithms.md (ALG-006) |
| Centroid Estimator | Profile | Compute Cognitive Centroid | ⚠️ Conceptual — FAISS centroid used as proxy | Algorithms/Behavior_Algorithms.md (ALG-009) |
| Temporal Updater | Profile | Integrate new observations with decay | ❌ Not implemented in prototype | Algorithms/Evidence_Algorithms.md (ALG-016) |
| Comparator | Comparison | Compute similarity scores | ✅ FAISS cosine similarity at 16μs validated | Algorithms/Similarity_Algorithms.md (ALG-024—028) |
| Feature Aligner | Comparison | Ensure compatible feature sets | ✅ Aligner tested on mismatched profiles | Algorithms/Similarity_Algorithms.md |
| Calibrator | Evidence | Transform scores to LRs | ⚠️ LR calibration framework designed | Algorithms/Attribution_Algorithms.md (ALG-017) |
| Fusion Engine | Evidence | Combine modality evidence | ❌ Single modality prototype only | Algorithms/Fusion_Algorithms.md (ALG-029—032) |
| Confidence Estimator | Evidence | Quantify attribution certainty | ⚠️ Empirical confidence from 15 experiments | Algorithms/Confidence_Algorithms.md (ALG-019—022) |
| Threshold Comparator | Decision | Apply decision thresholds | ⚠️ Manual threshold analysis performed | Algorithms/Decision_Algorithms.md (ALG-033) |
| Sequential Decision Engine | Decision | Deferred decisions pending evidence | ❌ Not implemented in prototype | Algorithms/Decision_Algorithms.md (ALG-036) |
| Report Generator | Decision | Produce standardized reports | ✅ Experimental results reports generated | Algorithms/Decision_Algorithms.md |

---

## Five Behavioral Modalities

| Modality | Input Data | Features | Source |
|---|---|---|---|
| **Forensic Stylometry** | Text content | Function-word frequencies, syntax patterns, vocabulary metrics | Framework/Framework_Modules.md (FWK-003) §2.1 |
| **Chrono-Profiling** | Timestamped activity | Circadian phase, inter-event intervals, burst parameters | Framework/Framework_Modules.md (FWK-003) §2.2 |
| **Terminal Execution Profiling** | Command logs | Command sequences, timing patterns, shell idioms | Framework/Framework_Modules.md (FWK-003) §2.3 |
| **Relational Network Analysis** | Social graph data | Graph topology, centrality, subgraph entropy | Framework/Framework_Modules.md (FWK-003) §2.4 |
| **Environmental Media Forensics** | File metadata | Organizational patterns, naming conventions | Framework/Framework_Modules.md (FWK-003) §2.5 |

---

## Fusion Architecture

| Strategy | Method | Algorithm | Source |
|---|---|---|---|
| **Score-Level** | Weighted combination of modality scores | ALG-030 | Algorithms/Fusion_Algorithms.md |
| **Feature-Level** | HOSVD on concatenated feature tensors | ALG-031 (PROPOSED) | Algorithms/Fusion_Algorithms.md |
| **Decision-Level** | Dempster-Shafer combination | ALG-032 | Algorithms/Fusion_Algorithms.md |

---

## Attribution Decision Framework

Attribution strength is expressed as a Likelihood Ratio (EQ-017):

```
LR = P(E | H_same) / P(E | H_diff)
```

| Condition | Conclusion | Source |
|---|---|---|
| LR ≥ τ_attribution | Same-source (attribution) | ALG-033 |
| LR ≤ τ_exclusion | Different-source (exclusion) | ALG-033 |
| τ_exclusion < LR < τ_attribution | Inconclusive | ALG-033 |

**Source**: Algorithms/Decision_Algorithms.md (ALG-033), Theory/Behavioral_Attribution_Theory.md (THY-003)

---

## Configuration Parameters

| Parameter | Options | Default | Source |
|---|---|---|---|
| Modalities | Any subset of {stylometry, chrono, terminal, network, media} | All five | Framework/Framework_Modules.md |
| Fusion strategy | score, decision, feature | score | Algorithms/Fusion_Algorithms.md |
| Calibration method | PAV, logistic regression | PAV | Algorithms/Attribution_Algorithms.md |
| Decision thresholds | Configurable per deployment | Standard forensic thresholds | Algorithms/Decision_Algorithms.md |
| Temporal decay half-life | Configurable | 90 days | Algorithms/Evidence_Algorithms.md |

---

## API Interfaces (Conceptual)

| Interface | Method | Input | Output | Source |
|---|---|---|---|---|
| Ingestion | POST /evidence | Raw data payload | Evidence ID | Specifications/API_Conceptual_Specifications.md (SPC-004) |
| Feature extraction | POST /extract | Evidence ID | Feature vector | Specifications/API_Conceptual_Specifications.md (SPC-004) |
| Profile management | POST /profile | Feature vectors | Profile ID | Specifications/API_Conceptual_Specifications.md (SPC-004) |
| Comparison | POST /compare | Questioned + Reference IDs | Score vector | Specifications/API_Conceptual_Specifications.md (SPC-004) |
| Attribution | POST /attribution | Comparison result | LR + Confidence | Specifications/API_Conceptual_Specifications.md (SPC-004) |
| Decision | POST /decide | LR + thresholds | Attribution conclusion | Specifications/API_Conceptual_Specifications.md (SPC-004) |

---

## Related Documents

- [Documentation/Architecture.md](Documentation/Architecture.md) — Complete architecture documentation
- [Documentation/Framework_Guide.md](Documentation/Framework_Guide.md) — Comprehensive framework reference
- [Framework/](Framework/) — Architecture, workflow, modules, pipeline specifications
- [Specifications/](Specifications/) — Component, API, and data model specifications
- [Diagrams/](Diagrams/) — Architecture and pipeline diagrams

---

## Prototype Architecture: Anubis Twitter v2.5

The validated prototype (Anubis Twitter v2.5) implements a subset of the full six-layer architecture, demonstrating the stylometric modality end-to-end with 15 executed experiments on 31 Egyptian Twitter accounts.

### Layer Mapping

| Theoretical Layer | Prototype Implementation | Status |
|---|---|---|
| **Data Layer** | Twitter API v2 data ingestion; tweet metadata extraction; chain-of-custody logging | ✅ Validated |
| **Feature Layer** | 372-dim stylometric feature vector (function-word frequencies, syntax patterns, vocabulary metrics); scikit-learn normalization pipeline | ✅ Validated |
| **Profile Layer** | Per-account profile construction via feature aggregation; FAISS index for efficient storage and retrieval | ✅ Validated |
| **Comparison Layer** | FAISS cosine similarity search; 16μs per query across 31 profiles; mean cross-user similarity 0.26 (σ = 0.12) | ✅ Validated |
| **Evidence Layer** | Score distribution analysis; empirical LR estimation from 15 experiments; single-modality (no fusion) | ⚠️ Partial |
| **Decision Layer** | Threshold-based attribution decisions; manual classification vs. automated; decision accuracy measured across 15 experiments | ⚠️ Partial |

### Prototype Metrics

| Metric | Value |
|---|---|
| Accounts profiled | 31 Egyptian Twitter |
| Feature dimensions | 372 |
| Experiments executed | 15 |
| Search latency | 16μs per query (FAISS) |
| Mean cross-user similarity | 0.26 (σ = 0.12) |
| Publication-ready claims | 6 / 10 |
| Modalities implemented | 1 (Forensic Stylometry) of 5 |

### Key Findings

1. **Stylometric fingerprints are persistent** — 372-dim feature vectors produce consistent within-user clustering across diverse topic contexts
2. **Cross-user separation is measurable** — mean cross-user cosine similarity of 0.26 provides clear separation for attribution
3. **FAISS enables real-time search** — 16μs query time supports operational-scale comparison
4. **6 of 10 empirical claims meet publication thresholds** — remaining 4 claims require additional data collection and analysis

### Next Architecture Phases

| Phase | Scope | Target Layers |
|---|---|---|
| **Phase 2** | Multi-modality integration (Chrono-Profiling) | Evidence, Feature |
| **Phase 3** | Full fusion engine (score-level, feature-level, decision-level) | Evidence |
| **Phase 4** | End-to-end automation with sequential decision procedures | Decision |
| **Phase 5** | Multi-platform adapters and cross-platform validation | Data, Feature |

**Source**: Anubis Twitter/reports/experimental_results/Experimental_Validation_Report.md, Anubis Twitter/reports/prototype/Prototype_Overview.md

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


