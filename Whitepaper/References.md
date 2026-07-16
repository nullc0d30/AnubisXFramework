# References

**AnubisX Framework — Complete Document Cross-Reference Index (Whitepaper Edition)**

---

**Document ID**: WHP-013  
**Version**: 1.0  
**Owner**: Ahmed Awad (NullC0d3)  
**Status**: ESTABLISHED  
**Dependencies**: None  
**Referenced Documents**: All WHP documents  
**Confidentiality**: PUBLIC (C0)  
**Last Review**: 2026-07-15

---

## Official DOI

DOI:
10.5281/zenodo.21393392

Persistent URL:
https://doi.org/10.5281/zenodo.21393392

This release is permanently archived on Zenodo under DOI: https://doi.org/10.5281/zenodo.21393392

---

## 1. Whitepaper Documents (Public)

| ID | Document | Description |
|----|----------|-------------|
| WHP-001 | [Executive_Summary.md](Executive_Summary.md) | High-level framework overview and validated prototype summary |
| WHP-002 | [Problem_Statement.md](Problem_Statement.md) | Digital attribution problem and requirements |
| WHP-003 | [Scientific_Background.md](Scientific_Background.md) | Scientific foundations and related work |
| WHP-004 | [Framework_Overview.md](Framework_Overview.md) | Framework architecture and prototype implementation |
| WHP-005 | [Core_Innovations.md](Core_Innovations.md) | Novel contributions of the framework |
| WHP-006 | [Applications.md](Applications.md) | Application domains and use cases |
| WHP-007 | [Limitations.md](Limitations.md) | Framework and prototype-specific limitations |
| WHP-008 | [Conclusion.md](Conclusion.md) | Summary and future directions |
| WHP-009 | [Prototype.md](Prototype.md) | Anubis Twitter v2.5 implementation details |
| WHP-010 | [Experimental_Validation.md](Experimental_Validation.md) | 15 experiments, results, publication readiness |
| WHP-011 | [Validated_Capabilities.md](Validated_Capabilities.md) | Empirically verified functionality |
| WHP-012 | [Future_Work.md](Future_Work.md) | Prioritized research and development roadmap |
| WHP-013 | [References.md](References.md) | This document — complete cross-reference index |
| — | [AnubisX_Whitepaper.md](AnubisX_Whitepaper.md) | Compiled master whitepaper (all sections) |

## 2. Framework-Internal References

### 2.1 Theory Documents

| ID | Document | Description |
|----|----------|-------------|
| THY-001 | Core_Theory.md | Foundational theory of behavioral identity attribution |
| THY-002 | Theory_of_Digital_Cognitive_Fingerprints.md | Cognitive metaphor and signal hierarchy |
| THY-003 | Behavioral_Attribution_Theory.md | LR-based attribution methodology |
| THY-004 | Identity_Attribution_Theory.md | Convergence, uncertainty, identity determination |
| THY-005 | Cross_Platform_Theory.md | Cross-platform normalization and linkage |

### 2.2 Axiom Documents

| Group | Document | Count | Scope |
|-------|----------|-------|-------|
| CORE | Core_Axioms.md | 5 | Identity Invariance, Traceability, Uniqueness, Involuntary Emission, Convergence |
| BEH | Behavior_Axioms.md | 8 | Cross-modal distinctness, signal stability, degradation, contextual influence |
| IDN | Identity_Axioms.md | 5 | Singularity, estimability, comparator, uncertainty boundedness |
| ATR | Attribution_Axioms.md | 6 | Multi-modal necessity, probabilistic output, quantified conclusion |
| EVI | Evidence_Axioms.md | 4 | Independence, convergence necessity, conflict transparency |
| RSN | Reasoning_Axioms.md | 3 | Conservative interpretation, hypothesis testing |

### 2.3 Algorithm Documents

| ID | Document | Algorithms |
|----|----------|------------|
| ALG-001 | Algorithm_Index.md | Master cross-reference |
| ALG-002 | Core_Algorithms.md | ALG-001—004 (core identity) |
| ALG-003 | Behavior_Algorithms.md | ALG-005—008 (behavioral signals) |
| ALG-004 | Identity_Algorithms.md | ALG-009—012 (identity determination) |
| ALG-005 | Evidence_Algorithms.md | ALG-013—016 (evidence integration) |
| ALG-006 | Attribution_Algorithms.md | ALG-017—019 (attribution reasoning) |
| ALG-007 | Confidence_Algorithms.md | ALG-020—023 (uncertainty quantification) |
| ALG-008 | Similarity_Algorithms.md | ALG-024—028 (similarity computation) |
| ALG-009 | Fusion_Algorithms.md | ALG-029—032 (multi-modal fusion) |
| ALG-010 | Decision_Algorithms.md | ALG-033—036, 041 (attribution decisions) |

### 2.4 Validation & Benchmarks

| ID | Document | Content |
|----|----------|---------|
| VLD-001 | Validation_Framework.md | 4-tier framework, 9 dimensions |
| VLD-002 | Validation_Criteria.md | 8 concept types, 38 criteria |
| VLD-005 | Evaluation_Methodology.md | 5 partitioning strategies, 6 protocols |
| BENCH-001 | Benchmark_Framework.md | Architecture, scoring, lifecycle |
| BENCH-002 | Benchmark_Catalog.md | Full specification for 24 benchmarks |

### 2.5 Experiment Documents

| ID | Document | Experiments |
|----|----------|-------------|
| EXP-001 | Experiment_Catalog.md | Type taxonomy and template |
| EXP-002 | Twitter_Experiments.md | 8 Twitter-specific experiments |
| EXP-003 | Facebook_Experiments.md | 7 Facebook-specific experiments |
| EXP-004 | Cross_Platform_Experiments.md | 5 cross-platform experiments |
| EXP-005 | Benchmark_Experiments.md | 5 benchmark experiments |
| EXP-006 | Stress_Testing.md | 6 stress/robustness experiments |
| EXP-007 | Ablation_Studies.md | 7 ablation/sensitivity experiments |

## 3. Experimental Evidence References

### 3.1 Evidence Documents (Internal)

| Document | Classification | Content |
|----------|---------------|---------|
| 01_Prototype_Evidence.md | C3 — RESTRICTED | 22 evidence items catalogued from code analysis |
| 02_Framework_Evidence_Map.md | C1 — INTERNAL | Mapping of code evidence to framework specifications |
| 03_Implemented_vs_Theory.md | C1 — INTERNAL | Gap analysis between implementation and theory |
| 04_Implemented_vs_Specification.md | C1 — INTERNAL | Gap analysis between implementation and specifications |
| 05_Prototype_Capabilities.md | C1 — INTERNAL | Detailed capability assessment (12 capabilities) |
| 06_Scientific_Evidence_Register.md | C0 — PUBLIC | 8 scientific claims with evidence status |
| 07_Experimental_Evidence_Register.md | C1 — INTERNAL | Experimental design, protocols, reproducibility assessment |

### 3.2 Core Prototype Evidence

| Evidence ID | Module | Strength | Relevance |
|-------------|--------|----------|-----------|
| E01 | StylometryEngine (`stylometry_core.py`) | **STRONG** | Core fingerprinting algorithm |
| E02 | ConfigBase (`config_base.py`) | **STRONG** | Demographic filtering knowledge base |
| E03 | EgyptianAccountVerifier (`egyptian_verifier.py`) | **STRONG** | Demographic filtering algorithm |
| E04 | BrowserProfileManager (`browser_profile_manager.py`) | **MODERATE** | Data collection infrastructure |
| E07 | GraphEngine (`graph_engine.py`) | **MODERATE** | Network analysis algorithms |
| E09 | TwitterPipeline (`pipeline.py`) | **STRONG** | End-to-end orchestration |

### 3.3 Scientific Claims Register

| Claim ID | Claim | Status | Confidence |
|----------|-------|--------|------------|
| SC-001 | Stylometric fingerprinting identifies users | PARTIALLY_SUPPORTED | LOW |
| SC-002 | Multi-model ensemble outperforms single | PARTIALLY_SUPPORTED | LOW |
| SC-003 | Demographic filtering improves accuracy | PARTIALLY_SUPPORTED | MEDIUM |
| SC-004 | Temporal features add discriminative power | PARTIALLY_SUPPORTED | VERY LOW |
| SC-005 | Network analysis reveals coordination | PARTIALLY_SUPPORTED | LOW |
| SC-006 | Cross-platform identity attribution | UNSUPPORTED | NONE |
| SC-007 | Versioned fingerprints track stability | PARTIALLY_SUPPORTED | LOW |
| SC-008 | Style shift detects deception | UNSUPPORTED | VERY LOW |

## 4. External Academic References

The following external works inform the theoretical foundations of the AnubisX Framework:

### 4.1 Stylometry & Authorship Attribution

- Burrows, J. F. (1987). "Word-patterns and story-shapes: The statistical analysis of narrative style." *Literary and Linguistic Computing*, 2(2), 61–70.
- Holmes, D. I. (1998). "The evolution of stylometry in humanities scholarship." *Literary and Linguistic Computing*, 13(3), 111–117.
- Stamatatos, E. (2009). "A survey of modern authorship attribution methods." *Journal of the American Society for Information Science and Technology*, 60(3), 538–556.
- Koppel, M., Schler, J., & Argamon, S. (2009). "Computational methods in authorship attribution." *Journal of the American Society for Information Science and Technology*, 60(1), 9–26.

### 4.2 Arabic Natural Language Processing

- Abdul-Mageed, M., et al. (2021). "MARBERT: Deep bidirectional transformers for Arabic." *ACL 2021*.
- Antoun, W., Baly, F., & Hajj, H. (2020). "AraBERT: Transformer-based model for Arabic language understanding." *LREC 2020*.
- Reimers, N. & Gurevych, I. (2019). "Sentence-BERT: Sentence embeddings using Siamese BERT-networks." *EMNLP 2019*.

### 4.3 Behavioral Forensics & Digital Attribution

- Abbasi, A. & Chen, H. (2008). "Writerpints: A stylometric approach to identity-level identification." *Journal of the American Society for Information Science and Technology*, 59(2), 209–224.
- Afroz, S., Brennan, M., & Greenstadt, R. (2012). "Detecting hoaxes, frauds, and deception in writing style online." *IEEE S&P 2012*.
- Almishari, M., et al. (2014). "Linguistic fingerprinting of anonymous posters." *ICWSM 2014*.

### 4.4 Evidence Theory & Multi-Modal Fusion

- Dempster, A. P. (1968). "A generalization of Bayesian inference." *Journal of the Royal Statistical Society*, Series B, 30(2), 205–232.
- Shafer, G. (1976). *A Mathematical Theory of Evidence*. Princeton University Press.
- Sentz, K. & Ferson, S. (2002). "Combination of evidence in Dempster-Shafer theory." *SAND 2002-0835*.

### 4.5 Legal Standards for Scientific Evidence

- Daubert v. Merrell Dow Pharmaceuticals, 509 U.S. 579 (1993).
- Federal Rules of Evidence, Rule 702 (2000).

---

*Third-party works cited herein remain the property of their respective authors and are subject to their own copyright.*

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
