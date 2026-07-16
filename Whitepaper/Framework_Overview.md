# Framework Overview

**AnubisX Framework — System Overview**

---

**Document ID**: WHP-004  
**Version**: 1.0  
**Owner**: Ahmed Awad (NullC0d3)  
**Status**: ESTABLISHED  
**Dependencies**: FWK-001—005  
**Referenced Documents**: AnubisX_Whitepaper.md  
**Confidentiality**: PUBLIC (C0)  
**Last Review**: 2026-07-14

---

## Official DOI

DOI:
10.5281/zenodo.21393392

Persistent URL:
https://doi.org/10.5281/zenodo.21393392

This release is permanently archived on Zenodo under DOI: https://doi.org/10.5281/zenodo.21393392

---

## 1. Architecture

The framework implements a five-stage pipeline:

```
Raw Data → Feature Extraction → Profile Construction → Profile Comparison → Evidence Integration → Decision
```

### 1.1 Feature Extraction

Each of the five modalities transforms raw behavioral data into structured feature vectors:

- **Stylometry**: Linguistic features (function words, syntax, vocabulary)
- **Chrono-Profiling**: Temporal features (circadian rhythms, intervals)
- **Terminal Profiling**: Interaction features (commands, timing, sequences)
- **Network Analysis**: Social features (graph topology, communication patterns)
- **Media Forensics**: Environmental features (organization, naming, metadata)

### 1.2 Profile Construction

Features are aggregated into modality-specific behavioral profiles — structured representations of observed behavior with statistical summaries.

### 1.3 Profile Comparison

Profiles are compared using modality-specific similarity functions producing similarity scores.

### 1.4 Evidence Integration

Scores are calibrated to Likelihood Ratios and fused across modalities using Dempster-Shafer Theory, producing a combined LR with uncertainty bounds.

### 1.5 Decision

The combined LR supports an attribution decision: identification, exclusion, or inconclusive.

## 2. Scientific Standards

The framework meets Daubert criteria for scientific evidence:
- Testable hypotheses
- Quantified error rates
- Peer-reviewed methodology
- Standardized protocols
- General acceptance in scientific community

## 6. Prototype Implementation

### 6.1 Anubis Twitter Intelligence v2.5

The framework has been implemented as a working prototype targeting Twitter/X platform data:

| Component | Implementation | Status |
|-----------|---------------|--------|
| StylometryEngine | `stylometry_core.py` — 3-model ensemble (MarBERT, AraBERT, MPNet) producing 372-dim fingerprints | **Verified** |
| FAISS Search | `pipeline.py` — IndexFlatIP with cosine similarity, ~16μs per query | **Verified** |
| EgyptianAccountVerifier | `egyptian_verifier.py` — 3-layer scoring with 200+ cultural indicators | **Verified** |
| GraphEngine | `graph_engine.py` — Directed graph, centrality metrics, coordination detection | **Implemented (untested)** |
| Dashboard | Django UI with 10 views, AnubisBackend service bridge | **Verified** |

### 6.2 Validated Capabilities

- **Stylometric fingerprinting**: 372-dimension vectors combining multilingual embeddings (256-dim), lexical features (16-dim), and character hash features (100-dim)
- **Demographic filtering**: 3-layer Egyptian verification (bio 60%, posts 40%) with bonus mechanisms
- **Vector search**: FAISS-based similarity search with versioned fingerprint database
- **Data pipeline**: End-to-end ingestion, fingerprinting, indexing, and reporting

### 6.3 Experimental Validation

15 experiments executed on 31 real Egyptian Twitter accounts. The prototype demonstrates functional feasibility of the framework's core claims while identifying specific areas requiring further development. See [Prototype.md](Prototype.md) and [Experimental_Validation.md](Experimental_Validation.md) for complete results.

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
