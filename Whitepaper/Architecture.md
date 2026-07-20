# Architecture: AnubisX Framework

**Document ID**: WHP-ARCH-001  
**Version**: 3.0.0  
**Classification**: PUBLIC (C0)  

---

## Official DOI

DOI: [10.5281/zenodo.21446923](https://doi.org/10.5281/zenodo.21446923)

This release is permanently archived on Zenodo under DOI: [https://doi.org/10.5281/zenodo.21446923](https://doi.org/10.5281/zenodo.21446923)

---

## 1. Overview

The AnubisX Framework architecture is organized as a six-layer, six-stage pipeline supporting three distinct workflows across five behavioral modalities. This document provides a high-level architectural overview; a comprehensive treatment is available in the Framework/ directory.

---

## 2. Six-Layer Architecture

| Layer | Function | Key Components |
|-------|----------|----------------|
| **Layer 1: Data Acquisition** | Ingest raw behavioral data from source platforms | Platform adapters, normalization, metadata extraction |
| **Layer 2: Feature Extraction** | Transform raw data into measurable features | NLP processors, timing analyzers, style metrics, interaction graphs |
| **Layer 3: Profile Construction** | Build behavioral profiles from feature vectors | Fingerprint generators, ensemble embedders, quality assessors |
| **Layer 4: Comparison Engine** | Compare profiles using similarity metrics | Distance functions, similarity scorers, FAISS search indices |
| **Layer 5: Evidence Evaluation** | Evaluate comparison results as evidence | LR calculators, weight assignors, error estimators |
| **Layer 6: Decision Framework** | Render identity decisions with confidence | Threshold classifiers, ACM, confidence intervals |

---

## 3. Six-Stage Pipeline

1. **Ingest** → 2. **Normalize** → 3. **Extract** → 4. **Profile** → 5. **Compare** → 6. **Decide**

---

## 4. Three Workflows

- **Identification**: 1:N search — given a query profile, find the best match in a gallery
- **Verification**: 1:1 comparison — determine if two profiles belong to the same identity
- **Forensic Comparison**: 1:1 with evidence grading — produce LR-based evidentiary weight

---

## 5. Five Behavioral Modalities

| Modality | Behavioral Signal | Current Status |
|----------|------------------|----------------|
| Stylometric | Writing style, vocabulary, syntax | ✅ Validated (prototype) |
| Temporal | Timing patterns, posting rhythms | ⚠️ Requires data |
| Interaction Graph | Social graph, @mention, retweet patterns | ⚠️ Requires data |
| Cross-Platform | Schema-mapped behavioral traces | ⚠️ Prototype (schema defined) |
| Multi-Modal Fusion | Ensemble of modalities | ⚠️ Partial (degraded) |

---

## 6. Component Catalog

| ID | Component | Layer | Status |
|----|-----------|-------|--------|
| CP-001 | StylometryEngine | 2-3 | ✅ Prototype |
| CP-002 | FAISS Similarity Search | 4 | ✅ Prototype |
| CP-003 | Identity Verifier | 4 | ⏳ Specified |
| CP-004 | GraphEngine | 2 | ⏳ Specified |
| CP-005 | EgyptianVerifier | 2-3 | ✅ Prototype |
| CP-006 | CrossPlatformNormalizer | 1 | ✅ Specified |

See Framework/Framework_Architecture.md for the complete 28-component catalog.

---

## 7. Prototype Architecture (Anubis Twitter v2.5)

The prototype implements layers 1-4 for the stylometric modality:

- **Data Acquisition**: 31 Egyptian Twitter account JSONs
- **Feature Extraction**: Lexical, syntactic, structural, content features → 372-dim vector
- **Profile Construction**: StylometryEngine producing normalized fingerprints
- **Comparison**: FAISS IndexFlatIP, cosine similarity, 16μs search

---

## 8. Relationship to Full Framework

| Component | Prototype Status | Full Framework Target |
|-----------|-----------------|----------------------|
| Stylometric | ✅ Complete | Multi-lingual expansion |
| Temporal | ❌ Not implemented | Date/time metadata required |
| Graph | ❌ Not implemented | Interaction dataset required |
| Fusion | ⚠️ Degraded (single model) | 3-model ensemble |
| Decision | ✅ Basic (similarity threshold) | Full LR + ACM |

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


