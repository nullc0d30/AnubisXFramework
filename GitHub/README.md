# AnubisX Framework

**A scientific methodology for behavioral identity attribution.**

[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)
[![Status: Theoretical + Prototype](https://img.shields.io/badge/Status-Theoretical%20%2B%20Prototype-blue)](ROADMAP.md)
[![Axioms](https://img.shields.io/badge/Axioms-16-8A2BE2)](Axioms/Core_Axioms.md)
[![Algorithms](https://img.shields.io/badge/Algorithms-37-success)](Algorithms/Algorithm_Catalog.md)
[![Experiments](https://img.shields.io/badge/Experiments-15%20Executed-brightgreen)](Anubis%20Twitter/reports/experimental_results/Executed_Experiments.md)
[![DOI](https://img.shields.io/badge/DOI-10.5281%2Fzenodo.21393392-blue)](https://doi.org/10.5281/zenodo.21446923)

---

## Overview

The AnubisX Framework is a formal scientific methodology for determining the identity of a human operator from their digital behavioral patterns. Unlike traditional attribution methods that rely on transient technical artifacts — IP addresses, device fingerprints, browser configurations — the framework measures **persistent human cognitive signatures** that are rooted in stable cognitive processing habits.

**Source**: Documentation/Overview.md §1, Theory/Core_Theory.md (THY-001)

The framework is a **complete theoretical specification** with a **validated prototype implementation**. The theoretical layer defines the axiomatic foundation, mathematical formalization, algorithm specifications, validation methodology, benchmark protocols, experiment designs, and case studies. The prototype layer (Anubis Twitter v2.5) implements a subset of the framework's stylometric fingerprinting and similarity search capabilities, with 15 executed experiments producing validated results across 31 Egyptian Twitter accounts.

**Source**: PROJECT_STATUS.md, PROJECT_COMPLETENESS_REPORT.md, Anubis Twitter/reports/experimental_results/

## Core Concepts

| Concept | Definition | Repository Source |
|---|---|---|
| **Cognitive Centroid** | The theoretical attractor of an individual's behavioral patterns in multi-dimensional feature space | Theory/Core_Theory.md (THY-001), HYP-CORE-001 |
| **Five Behavioral Modalities** | Forensic Stylometry, Chrono-Profiling, Terminal Execution Profiling, Relational Network Analysis, Environmental Media Forensics | Framework/Framework_Modules.md (FWK-003) |
| **Multi-Modal Fusion** | Combining evidence from independent behavioral signals for robust attribution | Algorithms/Fusion_Algorithms.md (ALG-029—032) |
| **Likelihood Ratio (LR)** | Statistical quantification of evidence strength: P(E\|H_same) / P(E\|H_diff) | Algorithms/Attribution_Algorithms.md (ALG-017), EQ-017 |
| **Identity Intelligence (IdINT)** | A proposed formal forensic discipline for behavioral attribution | Theory/Behavioral_Attribution_Theory.md (THY-003) |

**Source**: Documentation/Framework_Guide.md §1—2, Documentation/Overview.md §2

## How the Pipeline Works

The framework processes behavioral data through six defined stages, specified in Framework/Framework_Architecture.md (FWK-001) and Framework/Framework_Pipeline.md (FWK-004):

```
Ingestion → Feature Extraction → Profile Construction → Comparison → Evidence Evaluation → Decision
```

1. **Ingestion**: Raw digital traces are collected, validated, and metadata extracted
2. **Feature Extraction**: Modality-specific processors transform raw data into structured feature vectors (ALG-001—004)
3. **Profile Construction**: Features are aggregated into behavioral profiles with confidence bounds (ALG-006, ALG-016)
4. **Comparison**: Profiles are compared using similarity functions — Cosine, Euclidean, RBF, Pearson, Jaccard (ALG-024—028)
5. **Evidence Evaluation**: Scores are calibrated to Likelihood Ratios (ALG-017), weighted, and fused across modalities (ALG-029—032)
6. **Decision**: Attribution conclusions are produced with quantified uncertainty (ALG-033—036)

Three workflows are supported: **Identification**, **Verification**, and **Forensic Comparison**.

**Source**: Documentation/Architecture.md §2, Documentation/Framework_Guide.md §2

## Repository Structure

| Directory | Contents | Source |
|---|---|---|
| `Axioms/` | 16 formal axioms in 6 groups (CORE, BEH, ID, ATR, EVI, RSN) | Axioms/Axiom_Catalog.md |
| `Assumptions/` | 46 working assumptions in 6 categories | Assumptions/Assumption_Catalog.md |
| `Mathematics/` | 292 mathematical objects, 50 equations, 47 functions | Mathematics/Mathematical_Foundation.md |
| `Algorithms/` | 37+ algorithm specifications across 9 domains | Algorithms/Algorithm_Catalog.md |
| `Theory/` | 5 theoretical foundation documents | Theory/Theory_Index.md |
| `Framework/` | Architecture, workflow, modules, pipeline specifications | Framework/Framework_Index.md |
| `Specifications/` | Component, API, data model specifications | Specifications/Specification_Index.md |
| `Validation/` | 4-tier validation, 31 acceptance criteria | Validation/Validation_Framework.md (VLD-001) |
| `Benchmarks/` | 24 benchmarks, 30 baselines, 15 scenarios | Benchmarks/Benchmark_Index.md |
| `Experiments/` | 38 experiment designs across 6 domains | Experiments/Experiment_Index.md |
| `Case_Studies/` | 20 case studies across 4 domains | Case_Studies/Case_Study_Index.md |
| `Research/` | Research methodology, questions, limitations | Research/Research_Index.md |
| `Papers/` | Publication roadmap and 6 paper plans | Papers/Paper_Roadmap.md |
| `Documentation/` | 12 comprehensive public documentation files | Documentation/Overview.md |
| `Diagrams/` | Architecture and workflow diagram specifications | Diagrams/ |
| `Figures/` | Figure specifications | Figures/ |
| `Release/` | Release checklists and notes | Release/ |
| `IP/` | Intellectual property registers | IP/ |
| `Public/` | Whitepaper, website, GitHub, platform materials | Public/ |

**Source**: MASTER_INDEX.md, REPOSITORY_ORGANIZATION_GUIDE.md

## Getting Started

| Audience | Recommended Path |
|---|---|
| **Newcomers** | Documentation/Getting_Started.md → Documentation/FAQ.md → Documentation/Theory_Guide.md |
| **Researchers** | Documentation/Theory_Guide.md → Documentation/Mathematical_Model.md → Documentation/Algorithms.md → Documentation/Validation.md |
| **Developers** | Documentation/Architecture.md → Documentation/Framework_Guide.md → Documentation/Algorithms.md |
| **Forensic Practitioners** | Documentation/Framework_Guide.md → Documentation/Examples.md → Documentation/Validation.md |

## Documentation

| Document | Description |
|---|---|
| [Overview](Documentation/Overview.md) | Complete framework introduction |
| [Getting Started](Documentation/Getting_Started.md) | Step-by-step orientation |
| [Framework Guide](Documentation/Framework_Guide.md) | Comprehensive framework reference |
| [Theory Guide](Documentation/Theory_Guide.md) | Theoretical foundations |
| [Architecture](Documentation/Architecture.md) | System architecture and component design |
| [Mathematical Model](Documentation/Mathematical_Model.md) | Mathematical foundation reference |
| [Algorithms](Documentation/Algorithms.md) | Complete algorithm catalog |
| [Validation](Documentation/Validation.md) | Validation methodology |
| [FAQ](Documentation/FAQ.md) | Frequently asked questions |
| [Glossary](Documentation/Glossary.md) | Standardized terminology |
| [Examples](Documentation/Examples.md) | Case study walkthroughs |
| [References](Documentation/References.md) | Source document index |

## Current Status

All theoretical specifications are complete. The prototype implementation (Anubis Twitter v2.5) has been validated with 15 executed experiments producing verified results.

**Source**: PROJECT_STATUS.md, Anubis Twitter/reports/experimental_results/Experimental_Validation_Report.md

| Component | Status |
|---|---|
| Axiomatic foundation | Complete (16 axioms) |
| Mathematical foundation | Complete (292 objects, 50 equations) |
| Algorithm specifications | Complete (37 algorithms) |
| Validation framework | Complete (31 acceptance thresholds) |
| Benchmark framework | Complete (24 benchmarks) |
| Experiment designs | Complete (38 experiments — 15 executed) |
| Case studies | Complete (20 case studies) |
| Prototype implementation | ✅ Stylometric fingerprinting, FAISS search, Egyptian verification (15/15 experiments passed) |
| Empirical validation | **Partial** — 6/10 publication-ready claims; 4 require further validation |
| Full software implementation | **Next phase** |

## License

This work is licensed under [Creative Commons Attribution 4.0 International](LICENSE.md) (CC BY 4.0).

## Citation

If you use the AnubisX Framework in your research, please cite:

```bibtex
@software{anubisx2026framework,
  title = {AnubisX Framework: A Scientific Methodology for Behavioral Identity Attribution},
  year = {2026},
  url = {https://github.com/AnubisXFramework/AnubisXFramework},
  doi = {10.5281/zenodo.21446923}
}
```

Machine-readable citation metadata is available in [CITATION.cff](CITATION.cff).

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


