# Limitations

**AnubisX Framework — Acknowledged Limitations and Boundaries**

---

**Document ID**: WHP-007  
**Version**: 1.0  
**Project**: AnubisX Framework  
**Status**: ESTABLISHED  
**Dependencies**: RSR-003  
**Referenced Documents**: Research_Limitations.md  
**Confidentiality**: PUBLIC (C0)  
**Last Review**: 2026-07-14

---

## Official DOI

DOI: [10.5281/zenodo.21446923](https://doi.org/10.5281/zenodo.21446923)

This release is permanently archived on Zenodo under DOI: [https://doi.org/10.5281/zenodo.21446923](https://doi.org/10.5281/zenodo.21446923)

---

## 1. Fundamental Limitations

| Limitation | Description | Impact |
|---|---|---|
| Observational requirement | Sufficient behavioral data required | Attribution impossible with minimal data |
| Population dependence | Accuracy varies across populations | Calibration required per population |
| Temporal evolution | Patterns change over time | Profile updating necessary |
| Counter-forensic possibility | Determined adversaries can reduce signals | Attribution harder but not impossible |

## 2. Current State Limitations

| Limitation | Status |
|---|---|
| Empirical validation initiated | Prototype with 15 experiments completed |
| Software implementation exists | Anubis Twitter v2.5 prototype — 47 Python files |
| Limited operational testing | Single-platform (Twitter), single-population (Egyptian) |
| No peer-reviewed publications | Publication pipeline established, submissions pending |

## 2.3 Prototype-Specific Limitations

Validation of the Anubis Twitter Intelligence v2.5 prototype revealed the following specific limitations:

| Limitation | Impact | Root Cause |
|---|---|---|
| **Model authentication failures** | MarBERT/AraBERT fail to load via sentence_transformers; ensemble silently degrades to single MPNet model | HuggingFace authentication tokens not configured; model compatibility issues |
| **No timestamps in scraped data** | Temporal features (burstiness, hour/weekday entropy) produce meaningless values | Twitter scraper does not capture `created_at` field; uses `datetime.now()` |
| **No interaction data captured** | Graph analysis cannot build edge structures from @mentions | Scraper captures tweet text only; no mention metadata extracted |
| **Single-pass versioning** | Versioned fingerprint storage implemented but never exercised with multi-pass data | Pipeline runs as single pass; no repeated collections exist |
| **Small dataset** | Statistical power limited; results may not generalize beyond 31 Egyptian accounts | Convenience sample; no systematic sampling methodology |
| **No control group** | Cannot measure filtering accuracy or fingerprint discriminative power | All 31 accounts are Egyptian; no non-Egyptian baseline accounts |
| **FAISS dimension mismatch** | Legacy scripts (734-dim) incompatible with v2.5 pipeline (372-dim) causing search failures | Two feature extraction protocols without migration path |
| **No experiment tracking** | Results cannot be replicated without pinned dependencies, random seeds, or configuration freeze | No reproducibility infrastructure implemented |
| **Schema proliferation** | 4+ distinct database schemas without migration tool or unified access layer | Independent development of multiple pipeline versions |

## 3. Scope Boundaries

The framework does NOT address:

- **Offline behavior**: Digital traces only
- **Group attribution**: Individual operators, not groups
- **Real-time attribution**: Forensic analysis, not real-time identification
- **Deterministic identification**: Probabilistic conclusions with quantified uncertainty

## 4. Risk Mitigation

Each limitation has corresponding mitigation strategies documented in the full framework documentation.

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


