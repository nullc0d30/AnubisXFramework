# Future Work

**AnubisX Framework — Planned Research and Development Directions**

---

**Document ID**: WHP-012  
**Version**: 1.0  
**Project**: AnubisX Framework  
**Status**: ESTABLISHED  
**Dependencies**: WHP-009, WHP-010, WHP-011  
**Referenced Documents**: Prototype.md, Experimental_Validation.md, Validated_Capabilities.md  
**Confidentiality**: PUBLIC (C0)  
**Last Review**: 2026-07-15

---

## Official DOI

DOI: [10.5281/zenodo.21446923](https://doi.org/10.5281/zenodo.21446923)

This release is permanently archived on Zenodo under DOI: [https://doi.org/10.5281/zenodo.21446923](https://doi.org/10.5281/zenodo.21446923)

---

## 1. Accomplished (v1.0 Foundational Release)

The following items from the original research roadmap have been completed:

| Item | Status | Evidence |
|------|--------|----------|
| Core algorithm implementation (stylometry) | **Done** — 372-dim fingerprint pipeline operational | Prototype.md §3 |
| Profile construction and storage system | **Done** — Versioned SQLite schema with migration | Validated_Capabilities.md C03 |
| Similarity computation module | **Done** — FAISS IndexFlatIP at ~16μs/query | Validated_Capabilities.md C04 |
| Controlled stylometric experiments | **Done** — 15 experiments on 31 accounts | Experimental_Validation.md §2 |
| Demographic filtering implementation | **Done** — EgyptianAccountVerifier with 200+ indicators | Validated_Capabilities.md C02 |
| Dashboard and reporting | **Done** — 10 Django views, 3 report formats | Validated_Capabilities.md C07, C08 |

## 2. Immediate Priorities

### 2.1 Model Ensemble Resolution

| Task | Description | Priority |
|------|-------------|----------|
| Configure HuggingFace auth tokens | Resolve MarBERT/AraBERT authentication failures | **Critical** |
| Verify model compatibility | Test AraBERT-v2 and MarBERT with sentence-transformers API | **Critical** |
| Implement model caching | Cache downloaded models to avoid re-download | **High** |
| Validate ensemble weights | Empirically determine optimal 3-model weighting | **High** |

**Current blocker**: Experiment #2 (multi-model ensemble load) fails. Without all 3 models, the ensemble claim cannot be validated.

### 2.2 Temporal Data Collection

| Task | Description | Priority |
|------|-------------|----------|
| Fix scraper timestamp capture | Add `created_at` field extraction to `twitter_scraper_loggedin.py` | **High** |
| Collect timestamped dataset | Re-scrape accounts with timestamps enabled | **High** |
| Validate temporal features | Run temporal feature extraction on real timestamps | **High** |
| Ablation study | Compare attribution accuracy with/without temporal features | **Medium** |

**Current blocker**: All scraped data has `datetime.now()` as timestamp, making temporal features (Claim SC-004) untestable.

### 2.3 Interaction Dataset for Graph Analysis

| Task | Description | Priority |
|------|-------------|----------|
| Capture mention metadata | Extract @mentions, reply-to, retweet metadata during scraping | **High** |
| Build labeled coordination dataset | Collect accounts with known coordination patterns | **Medium** |
| Validate GraphEngine | Run centrality and coordination detection on real interaction data | **Medium** |
| Implement Louvain clustering | Replace connected components with overlapping community detection | **Medium** |

**Current blocker**: No interaction metadata captured; GraphEngine validated for structure only.

## 3. Short-Term Development

### 3.1 Multi-Pass Versioning Experiments

| Task | Description | Priority |
|------|-------------|----------|
| Longitudinal data collection | Collect fingerprints for same accounts at 3+ time points | **High** |
| Validate stability tracking | Verify cosine similarity stability metric across versions | **High** |
| Implement drift detection | Define thresholds for meaningful behavioral change alerts | **Medium** |

**Current blocker**: All experiments are single-pass; versioning system has never been exercised with multi-pass data.

### 3.2 FAISS Dimension Consistency

| Task | Description | Priority |
|------|-------------|----------|
| Unify dimension across scripts | Ensure all scripts use consistent 372-dim vectors | **Critical** |
| Deprecate legacy 734-dim path | Remove or migrate features.py-based scripts | **High** |
| Add dimension validation | Runtime check that FAISS index dimension matches pipeline dimension | **High** |

**Current blocker**: Experiment #6 (FAISS dimension consistency) fails. Legacy scripts use 734-dim, creating a broken search chain.

### 3.3 Reproducibility Infrastructure

| Task | Description | Priority |
|------|-------------|----------|
| Create requirements.txt | Pin all dependency versions | **Critical** |
| Set random seeds | Add `np.random.seed()`, `torch.manual_seed()` to all pipelines | **Critical** |
| Pin model revisions | Specify HuggingFace model revision hashes | **High** |
| Create data manifest | Checksums for all raw JSON files | **High** |
| Configuration freeze | Document all parameters at time of experiment | **Medium** |
| Hardware specification | Document CPU, RAM, storage requirements | **Medium** |

## 4. Medium-Term Development

### 4.1 Multi-Platform Expansion

| Task | Description | Priority |
|------|-------------|----------|
| Facebook data collection | Resolve Facebook scraping; collect real data | **Medium** |
| Cross-platform vector comparison | Implement identity matching across Twitter/Facebook | **Medium** |
| Platform adapter standardization | Refactor PlatformBase into production-grade abstraction | **Low** |

**Current blocker**: Facebook adapter infrastructure exists but has never been successfully executed.

### 4.2 Full Framework Implementation

| Task | Description | Priority |
|------|-------------|----------|
| Chrono-profiling modality | Implement temporal analysis as standalone modality | **Medium** |
| Terminal profiling modality | Implement interaction sequence analysis | **Low** |
| Network analysis modality | Expand GraphEngine with full social network analysis | **Medium** |
| Media forensics modality | Implement environmental/organizational feature extraction | **Low** |
| Multi-modal fusion engine | Implement Dempster-Shafer evidence integration | **Medium** |
| Likelihood Ratio calibration | Implement LR computation from similarity scores | **Medium** |

### 4.3 All 24 Remaining Experiments

| Experiment Group | Count | Current Status |
|----------------|-------|----------------|
| Twitter Experiments (EXP-002) | 8 | 15 executed (prototype) |
| Facebook Experiments (EXP-003) | 7 | 0 — Facebook not operational |
| Cross-Platform Experiments (EXP-004) | 5 | 0 — Cross-platform not implemented |
| Benchmark Experiments (EXP-005) | 5 | 0 — Implementation pending |
| Stress Testing (EXP-006) | 6 | 0 — Infrastructure pending |
| Ablation Studies (EXP-007) | 7 | 0 — Framework pending |

**Total remaining**: 24 experiments across 6 categories, requiring multi-platform support, full framework implementation, and production-grade infrastructure.

## 5. Long-Term Vision

### 5.1 Publication Pipeline

| Phase | Target | Claims | Timeline |
|-------|--------|--------|----------|
| Phase 1 | Feasibility/methodology publication | SC-001, SC-003, SC-005, SC-007 | Q3 2026 |
| Phase 2 | Ensemble + temporal analysis | SC-002, SC-004 | Q1 2027 |
| Phase 3 | Multi-modal fusion | SC-009, SC-010 | Q3 2027 |
| Phase 4 | Cross-platform identity | SC-006, deception SC-008 | Q1 2028 |

### 5.2 Discipline Establishment

- Establish Identity Intelligence as recognized forensic discipline
- Develop professional certification and training programs
- Contribute to legal standards for behavioral evidence admissibility

### 5.3 Ecosystem Development

- Open-source reference implementation
- Community-contributed modality modules
- Third-party validation programs
- Integration with existing forensic workflows

## 6. Updated Timeline

```
Q3 2026: Resolve model auth + timestamp capture + FAISS dimension fix
Q4 2026: Multi-pass experiments + reproducibility infrastructure
Q1 2027: Facebook platform + cross-platform comparison (basic)
Q2 2027: Chrono-profiling + network analysis modalities
Q3 2027: Multi-modal fusion engine + Phase 1 publications
Q4 2027: Remaining experiments + Phase 2 publications
2028+:   Discipline establishment + ecosystem development
```

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


