# Theory Guide

**AnubisX Framework — Theoretical Foundations of Behavioral Identity Attribution**

---

## Official DOI

DOI: [10.5281/zenodo.21446923](https://doi.org/10.5281/zenodo.21446923)

This release is permanently archived on Zenodo under DOI: [https://doi.org/10.5281/zenodo.21446923](https://doi.org/10.5281/zenodo.21446923)

---

## 1. Introduction

This guide presents the theoretical foundations of the AnubisX Framework. It covers the Cognitive Centroid theory, the 16 formal axioms, 20 hypotheses, and 18 design principles, the 46 assumptions, Identity Intelligence (IdINT) as a proposed discipline, the five tracking modalities and their theoretical basis, the signal decomposition model, and the Likelihood Ratio framework.

The complete theoretical specification is documented in the Theory/ directory (THY-001 through THY-005).

---

## 2. Cognitive Centroid Theory

### 2.1 Core Concept

The Cognitive Centroid (HYP-CORE-001) is the central theoretical construct of the AnubisX Framework. It is defined as the unique, mathematically stable attractor in behavioral feature space toward which an individual's observable behavioral patterns converge over time.

Formally, for an individual i, the Cognitive Centroid C_i is the expected value of their behavioral feature vector f_i(t) over time and contexts:

```
C_i = E_{t,c}[f_i(t, c)]
```

where t indexes time and c indexes context.

### 2.2 Key Properties

| Property | Description | Axiom |
|---|---|---|
| **Uniqueness** | No two individuals share the same centroid | HYP-CORE-001 |
| **Persistence** | Stable across technical infrastructure changes | HYP-CORE-002 |
| **Convergence** | Observable patterns converge toward centroid with sufficient observations | HYP-CORE-005 |
| **Multi-modality** | Expressed across all behavioral modalities | HYP-CORE-003 |
| **Involuntariness** | Largely outside conscious control | HYP-BEH-004 |
| **Stability** | Changes slowly (if at all) through learning and habituation | HYP-BEH-002 |

### 2.3 Theoretical Support

The Cognitive Centroid is supported by established science:

| Field | Support |
|---|---|
| **Cognitive Psychology** | Stable individual differences in cognitive processing (attention, memory, executive function) |
| **Psycholinguistics** | Linguistic idiolect — each individual has unique patterns of language use |
| **Procedural Memory** | Motor and cognitive routines are encoded as stable procedural memories |
| **Signal Detection Theory** | Individuals have stable response criteria and sensitivity profiles |
| **Behavioral Biometrics** | Keystroke dynamics, gait analysis, and voice recognition demonstrate individual-specific patterns |

### 2.4 Centroid Estimation

Per ALG-009, the Cognitive Centroid is estimated as the mean of observed feature vectors:

```
C_i_hat = (1/n) * sum(f_i_j)
```

where f_i_j are n feature vectors from individual i. The estimate converges at rate O(1/sqrt(n)) per HYP-CORE-005 (Asymptotic Convergence).

---

## 3. The 31 Formal Axioms

The framework's axiomatic system comprises 16 formal axioms organized into 6 groups, supported by 20 research hypotheses and 18 design principles. Each axiom states a fundamental truth that is accepted without proof within the framework.

### 3.1 Core Axioms (HYP-CORE-001 — 005)

| ID | Name | Statement |
|---|---|---|
| HYP-CORE-001 | Identity Invariance | An individual's cognitive processing habits converge toward a unique, mathematically stable attractor — the Cognitive Centroid |
| HYP-CORE-002 | Cognitive Persistence | Behavioral patterns persist across changes in technical infrastructure |
| HYP-CORE-003 | Multi-Modal Convergence | No single modality provides definitive attribution; convergence of multiple independent signals is required |
| HYP-CORE-004 | Observational Bound | The empirical error rate of any attribution system is bounded below by the quantity and quality of observations |
| HYP-CORE-005 | Behavioral Identity as Emergent Property | Identity attribution emerges from the convergence of independent behavioral measurements |

### 3.2 Behavioral Axioms (HYP-BEH-001 — 006)

Characterize the nature, measurability, and structure of human behavioral signals:

| ID | Name | Statement |
|---|---|---|
| HYP-BEH-001 | Involuntary Signal Emission | Human operators involuntarily emit behavioral signatures during digital interaction |
| HYP-BEH-002 | Signal Stability | Behavioral signals exhibit temporal stability over meaningful forensic timeframes |
| HYP-BEH-003 | Signal Degradation | Behavioral signals degrade over time through drift, learning, and habituation |
| HYP-BEH-004 | Deliberate Modification Cost | Conscious modification of behavioral signals imposes cognitive load, degrading other signals |
| HYP-BEH-005 | Involuntary Signal Hierarchy | More involuntary signals (function words, timing) carry higher forensic value than voluntary signals (topic choice) |
| HYP-BEH-006 | Cross-Modal Signal Independence | Behavioral signals across different modalities exhibit approximate independence |

### 3.3 Identity Axioms (HYP-ID-001 — 005)

Formalize the relationship between behavioral signals and identity:

| ID | Name | Statement |
|---|---|---|
| HYP-ID-001 | Identity Singularity | Each individual possesses exactly one Cognitive Centroid |
| HYP-ID-002 | Profile Estimability | The Cognitive Centroid can be estimated from finite observations |
| HYP-ID-003 | Baseline Refresh Necessity | Behavioral baselines must be periodically refreshed to account for drift |
| HYP-ID-004 | Identity Resolution Uniqueness | Cross-platform identity resolution is unique (one individual maps to one multi-modal profile) |
| HYP-ID-005 | Identity Profile Boundaries | Identity profiles have measurable boundaries in feature space |

### 3.4 Attribution Axioms (DP-ATR-001 — 005)

Define the logical structure of attribution claims:

| ID | Name | Statement |
|---|---|---|
| DP-ATR-001 | Multi-Modal Necessity | Attribution conclusions must be based on at least two independent behavioral modalities |
| DP-ATR-002 | Probabilistic Output | Attribution conclusions must be expressed as probabilities, not certainties |
| DP-ATR-003 | Quantified Conclusion | All attribution conclusions must include quantified uncertainty |
| DP-ATR-004 | Inconclusive Admissibility | Inconclusive outcomes are valid and must be clearly distinguished from negative outcomes |
| DP-ATR-005 | Reproducible Procedure | All attribution procedures must be reproducible by independent examiners |

### 3.5 Evidence Axioms (DP-EVI-001 — 005)

Establish standards for evidence collection and handling:

| ID | Name | Statement |
|---|---|---|
| DP-EVI-001 | Evidential Independence | Evidence sources should be independent unless dependence is explicitly modeled |
| DP-EVI-002 | Convergence Necessity | Attribution requires convergence of independent evidence streams |
| DP-EVI-003 | Conflict Transparency | Conflicts between evidence sources must be reported, not hidden |
| DP-EVI-004 | Weighted Combination | Evidence must be weighted by quality, relevance, and recency before combination |
| DP-EVI-005 | Falsifiability Requirement | All attribution claims must be empirically falsifiable |

### 3.6 Reasoning Axioms (DP-RSN-001 — 005)

Govern the inferential logic connecting evidence to conclusions:

| ID | Name | Statement |
|---|---|---|
| DP-RSN-001 | Conservative Interpretation | The framework must be biased against false positives (conservative attribution) |
| DP-RSN-002 | Hypothesis Testing | Attribution is framed as hypothesis testing (H_p vs. H_d) |
| DP-RSN-003 | Empirical Grounding | All probabilistic estimates must be empirically grounded |
| DP-RSN-004 | Methodological Transparency | All methodological choices must be explicitly documented |
| DP-RSN-005 | Alternative Hypothesis Consideration | All reasonable alternative hypotheses must be considered and addressed |

---

## 4. The 46 Assumptions

The framework depends on 46 assumptions organized into 6 categories. Unlike axioms (accepted as fundamental), assumptions have varying empirical support:

| Category | Count | Status Distribution |
|---|---|---|
| Core (ASSUMP-CORE) | 9 | 2 VERIFIED, 2 POSTULATE, 5 HYPOTHESIS |
| Behavioral (ASSUMP-BEH) | 12 | 5 VERIFIED, 3 HYPOTHESIS, 3 CONTINGENT, 1 CONTINGENT |
| Identity (ASSUMP-ID) | 6 | 1 POSTULATE, 2 HYPOTHESIS, 3 CONTINGENT |
| Data (ASSUMP-DAT) | 7 | 3 HYPOTHESIS, 4 CONTINGENT |
| Platform (ASSUMP-PLT) | 6 | 2 VERIFIED, 2 HYPOTHESIS, 2 CONTINGENT |
| AI / ML (ASSUMP-AI) | 6 | 1 VERIFIED, 1 HYPOTHESIS, 4 CONTINGENT |

### Status Legend

| Status | Meaning | Count |
|---|---|---|
| VERIFIED | Empirically supported by published research | 10 (22%) |
| HYPOTHESIS | Proposed but not yet empirically verified | 16 (35%) |
| POSTULATE | Accepted as foundational without proof | 3 (7%) |
| CONTINGENT | Conditionally accepted pending validation | 17 (37%) |
| REFUTED | Previously assumed but contradicted by evidence | 0 (0%) |

### Key Assumptions Summary

**VERIFIED assumptions** (strongest empirical support):
- ASSUMP-CORE-004: Temporal Stability
- ASSUMP-CORE-005: Involuntary Leakage
- ASSUMP-BEH-001: Unconscious Stylometric Emission
- ASSUMP-BEH-002: Stylometric Cross-Context Stability
- ASSUMP-BEH-003: Circadian Rhythm Persistence
- ASSUMP-BEH-006: Device Artifact Persistence
- ASSUMP-BEH-009: Keystroke Dynamic Uniqueness
- ASSUMP-BEH-012: AI-Generated Text Artifacts
- ASSUMP-PLT-003: Toolchain Artifact Consistency
- ASSUMP-PLT-006: Hardware Characteristic Stability

**Critical HYPOTHESIS assumptions** (require validation):
- ASSUMP-CORE-002: Cognitive Uniqueness
- ASSUMP-CORE-007: Cross-Modal Independence
- ASSUMP-ID-002: Behavioral Signature Uniqueness
- ASSUMP-ID-003: Cross-Platform Signature Consistency
- ASSUMP-DAT-004: Noise Characterizability
- ASSUMP-PLT-005: Core Signal Platform Independence

---

## 5. Identity Intelligence (IdINT) as a Proposed Discipline

Identity Intelligence (IdINT) is proposed as a formal forensic discipline alongside DNA analysis, fingerprinting, firearm examination, and document analysis.

### 5.1 The Case for IdINT

Traditional forensic disciplines analyze physical traces left by the human body:
- **DNA**: Biological material
- **Fingerprints**: Friction ridge skin impressions
- **Ballistics**: Tool marks on ammunition
- **Handwriting**: Motor control patterns

IdINT argues that **cognitive traces** — patterns of language, timing, interaction, and organization — are equally individual-specific and should be recognized as a distinct class of forensic evidence.

### 5.2 Scientific Basis

IdINT draws on established science:

| Foundation | Contribution |
|---|---|
| Cognitive psychology | Stable individual differences in attention, memory, executive function |
| Psycholinguistics | Linguistic idiolect and unconscious language processing |
| Forensic science | LR framework, Daubert standard, error rate methodology |
| Biometrics | Individual identification from measurable traits |
| Signal detection theory | Decision framework under uncertainty |

### 5.3 Meeting Daubert Standards

The framework is designed to meet the Daubert standard for admissibility of scientific evidence:

| Daubert Factor | AnubisX Response |
|---|---|
| Testability | 37 algorithms, 38 experiments, falsifiable predictions |
| Peer review | Publication pipeline (6 papers planned) |
| Error rate | 31 acceptance criteria, 13 accuracy metrics, 23 total metrics |
| Standards | Standardized protocols, reproducibility requirements |
| General acceptance | Novel discipline — acceptance built through publication |

---

## 6. The Five Tracking Modalities

### 6.1 Forensic Stylometry

**Theoretical basis**: Linguistic idiolect — each individual has stable, unique patterns of language use that emerge from their language acquisition history, cognitive processing style, and habitual linguistic choices.

**Key signals**: Function-word frequencies, syntactic structure preferences, vocabulary richness, readability metrics, punctuation habits.

**Supporting axioms**: HYP-BEH-001 (Involuntary Signal Emission), ASSUMP-BEH-001 (Unconscious Stylometric Emission), ASSUMP-BEH-002 (Stylometric Cross-Context Stability).

### 6.2 Chrono-Profiling

**Theoretical basis**: Temporal cognition — individuals have stable circadian rhythms, attentional cycles, and temporal habits that manifest in their digital activity patterns.

**Key signals**: Circadian activity rhythms, inter-event timing distributions, response time patterns, temporal clustering, periodicity.

**Supporting axioms**: HYP-BEH-002 (Signal Stability), ASSUMP-BEH-003 (Circadian Rhythm Persistence), ASSUMP-CORE-004 (Temporal Stability).

### 6.3 Terminal Execution Profiling

**Theoretical basis**: Procedural memory and motor programming — individuals develop stable patterns of human-machine interaction through repeated practice, encoded as procedural memories.

**Key signals**: Command sequences, navigation paths, input timing and rhythm, error patterns, tool selection preferences.

**Supporting axioms**: HYP-BEH-004 (Deliberate Modification Cost), ASSUMP-BEH-004 (CLI Habit Deep Encoding), ASSUMP-BEH-007 (Typo Recovery Involuntariness).

### 6.4 Relational Network Analysis

**Theoretical basis**: Social cognition — individuals have stable patterns of relationship formation, communication, and group dynamics that reflect their social cognitive style.

**Key signals**: Network topology, communication frequency, group affiliations, information propagation patterns, network roles.

**Supporting axioms**: HYP-BEH-006 (Cross-Modal Signal Independence), ASSUMP-BEH-005 (Network Structure Individuality).

### 6.5 Environmental Media Forensics

**Theoretical basis**: Organizational cognition — individuals develop stable habits of digital environment organization through repeated practice, reflecting their cognitive style.

**Key signals**: File system structure, naming conventions, metadata habits, configuration preferences, workflow patterns.

**Supporting axioms**: ASSUMP-BEH-006 (Device Artifact Persistence), ASSUMP-PLT-003 (Toolchain Artifact Consistency).

---

## 7. Signal Decomposition Model

The framework models observed behavioral data as a composite of four components:

```
y = y_cog + y_ctx + y_temp + y_noise
```

| Component | Symbol | Source | Properties |
|---|---|---|---|
| Cognitive signal | y_cog | Individual's stable cognitive patterns | Target of attribution; unique, persistent |
| Context effect | y_ctx | Environmental/technical context | Systematic, normalizable (ALG-008) |
| Temporal effect | y_temp | Time-varying changes (learning, drift) | Slowly varying, trackable (ALG-016) |
| Measurement noise | y_noise | Acquisition noise, sampling error | Zero-mean, bounded variance |

### Decomposition Goal

ALG-005 (Behavioral Signal Decomposition) aims to isolate y_cog from the confounds, with a target variance reduction of >= 30% (AC-002D).

---

## 8. Likelihood Ratio Framework

Attribution strength is quantified using the Likelihood Ratio:

```
LR = P(E | H_p) / P(E | H_d)
```

Where:
- E = observed behavioral evidence
- H_p = same-source hypothesis (questioned and reference samples from same individual)
- H_d = different-source hypothesis (questioned and reference samples from different individuals)

### Interpretation Scale

| LR Range | Evidence Strength |
|---|---|
| LR > 100 | Very strong support for same-source |
| 10 < LR <= 100 | Strong support for same-source |
| 3 < LR <= 10 | Moderate support for same-source |
| 1 < LR <= 3 | Limited support for same-source |
| LR = 1 | No support for either hypothesis |
| 0.33 < LR < 1 | Limited support for different-source |
| 0.1 < LR <= 0.33 | Moderate support for different-source |
| 0.01 < LR <= 0.1 | Strong support for different-source |
| LR <= 0.01 | Very strong support for different-source |

### Multi-Modal LR Fusion

For M independent modalities, the combined LR is:

```
LR_combined = product(LR_m ^ w_m)
```

where w_m are modality weights normalized such that sum(w_m) = 1.

---

## 9. Key References

### Theory Documents (Theory/)

| ID | Document | Content |
|---|---|---|
| THY-001 | Core_Theory.md | Foundational theory, Identity Invariance Principle |
| THY-002 | Theory_of_Digital_Cognitive_Fingerprints.md | Cognitive fingerprint science |
| THY-003 | Behavioral_Attribution_Theory.md | Attribution logic and LR framework |
| THY-004 | Identity_Attribution_Theory.md | Identity constructs and processes |
| THY-005 | Cross_Platform_Theory.md | Cross-platform identity resolution |

### Axioms Documents (Axioms/)

| Document | Content |
|---|---|
| Core_Axioms.md | HYP-CORE-001 — 005 |
| Behavior_Axioms.md | HYP-BEH-001 — 006 |
| Identity_Axioms.md | HYP-ID-001 — 005 |
| Attribution_Axioms.md | DP-ATR-001 — 005 |
| Evidence_Axioms.md | DP-EVI-001 — 005 |
| Reasoning_Axioms.md | DP-RSN-001 — 005 |

### Assumptions Documents (Assumptions/)

| Document | Assumptions |
|---|---|
| Core_Assumptions.md | ASSUMP-CORE-001 — 009 |
| Behavioral_Assumptions.md | ASSUMP-BEH-001 — 012 |
| Identity_Assumptions.md | ASSUMP-ID-001 — 006 |
| Data_Assumptions.md | ASSUMP-DAT-001 — 007 |
| Platform_Assumptions.md | ASSUMP-PLT-001 — 006 |
| AI_Assumptions.md | ASSUMP-AI-001 — 006 |

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


