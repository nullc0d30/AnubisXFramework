# Prototype Implementation

**AnubisX Framework — Anubis Twitter Intelligence Prototype v2.5**

---

**Document ID**: WHP-009  
**Version**: 1.0  
**Project**: AnubisX Framework  
**Status**: ESTABLISHED  
**Dependencies**: WHP-004  
**Referenced Documents**: Framework_Overview.md, Experimental_Validation.md, Validated_Capabilities.md  
**Confidentiality**: PUBLIC (C0)  
**Last Review**: 2026-07-15

---

## Official DOI

DOI: [10.5281/zenodo.21446923](https://doi.org/10.5281/zenodo.21446923)

This release is permanently archived on Zenodo under DOI: [https://doi.org/10.5281/zenodo.21446923](https://doi.org/10.5281/zenodo.21446923)

---

## 1. Overview

The Anubis Twitter Intelligence Prototype v2.5 is the first software implementation of the AnubisX Framework. It implements the stylometric modality end-to-end: data collection, feature extraction, fingerprint construction, similarity search, demographic filtering, and visualization. The prototype comprises 47 Python files organized into 5 packages.

## 2. Architecture

```
Shared Modules          Twitter Package           Analysis Package        UI Package
┌─────────────────┐    ┌──────────────────┐      ┌────────────────┐      ┌──────────────┐
│ StylometryEngine│───▶│ Scrapers         │      │ GraphEngine    │      │ Django Views │
│ (stylometry_core│    │ (twitter_scraper │      │ (graph_engine) │      │ (10 views)   │
│  .py)           │    │  _loggedin.py)   │      │                │      │              │
│                 │    │                  │      │ Centrality:    │      │ Services:    │
│ 3-model ensemble│    │ Session Manager  │      │ • Degree       │      │ AnubisBackend│
│ → 372-dim vec   │    │                  │      │ • Betweenness  │      │              │
│                 │    │ Pipeline:        │      │ • Eigenvector  │      │ Reports:     │
│ EgyptianVerifier│    │ run_all.py       │      │                │      │ Excel, HTML, │
│ (egyptian_      │    │                  │      │ Coordination:  │      │ Markdown     │
│  verifier.py)   │    │ FAISS Search     │      │ Connected comps│      │              │
│                 │    │ (pipeline.py)    │      │                │      │              │
│ ConfigBase      │    │                  │      │                │      │              │
│ (200+ Egyptian  │    │ SQLite Storage   │      │                │      │              │
│  indicators)    │    │ (versioned)      │      │                │      │              │
└─────────────────┘    └──────────────────┘      └────────────────┘      └──────────────┘
```

### 2.1 Shared Modules (6 files)

| Module | File | Purpose |
|--------|------|---------|
| StylometryEngine | `stylometry_core.py` (181 LOC) | 3-model ensemble fingerprinting, 372-dim vectors |
| ConfigBase | `config_base.py` (192 LOC) | 200+ Egyptian cultural indicators, thresholds |
| EgyptianAccountVerifier | `egyptian_verifier.py` (207 LOC) | 3-layer demographic scoring |
| BrowserProfileManager | `browser_profile_manager.py` (63 LOC) | Chrome stealth configuration |
| PlatformBase | `platform_base.py` (51 LOC) | Abstract cross-platform interface |
| Utils | `utils.py` (81 LOC) | Text cleaning, Arabic normalization |

### 2.2 Twitter Package

| Module | File | Purpose |
|--------|------|---------|
| TwitterAdapter | `adapter.py` (63 LOC) | Platform integration |
| Pipeline | `vector/pipeline.py` (214 LOC) | Versioned fingerprinting, FAISS index, orchestration |
| SessionManager | `scrapers/session_manager.py` (92 LOC) | Login session management |
| TwitterScraperLogged | `scrapers/twitter_scraper_loggedin.py` (133 LOC) | Profile/tweet scraping via Selenium |

### 2.3 Analysis Package

| Module | File | Purpose |
|--------|------|---------|
| GraphEngine | `analysis/graph_engine.py` (186 LOC) | Network graph construction, centrality, coordination detection |

### 2.4 UI Package

| Module | File | Purpose |
|--------|------|---------|
| Views | `UI/anubis_x/core/views.py` (70 LOC) | 10 Django views |
| Services | `UI/anubis_x/core/services.py` (216 LOC) | Backend data access bridge |

### 2.5 Root Scripts (9 files)

| Script | Lines | Purpose |
|--------|-------|---------|
| `features.py` | 300 | Legacy 734-dim single-model fingerprinting |
| `extract_fp.py` | 426 | v2.3 fingerprint pipeline with deception detection |
| `extract_all_fingerprints.py` | 350 | Standalone batch fingerprint extraction |
| `build_fingerprints.py` | 48 | Batch fingerprint builder (legacy) |
| `faiss_build.py` | 34 | FAISS index builder (legacy) |
| `faiss_search.py` | 21 | FAISS search (legacy) |
| `db_init.py` | 43 | Database initialization |
| `ingest_from_raw.py` | 31 | JSON data ingestion |
| `run_all.py` | 15 | Pipeline orchestrator |

## 3. Stylometric Fingerprint Pipeline

### 3.1 Feature Extraction (372-dim)

The pipeline produces a 372-dimension fingerprint vector per user through four stages:

**Stage 1 — Multilingual Embedding (256-dim)**
- Three models: MarBERT (weight 0.45), AraBERT (weight 0.35), MPNet (weight 0.20)
- Each produces variable-dimension embeddings → projected to 256-dim via linear projection
- Weighted average combines the three projected vectors

**Stage 2 — Lexical Features (16-dim)**
- Type-Token Ratio (TTR)
- Average word length
- Punctuation ratio
- Emoji ratio
- Top 100 character 3-grams (hash-count vector)
- Top 50 most frequent words

**Stage 3 — Temporal Features (5 dims, within the 16-dim stats)**
- Burstiness (coefficient of variation of inter-post intervals)
- Hour entropy (uniformity of posting across 24 hours)
- Weekday entropy (uniformity across 7 days)
- Average inter-post interval
- Inter-post interval variance

**Stage 4 — Vector Assembly**
- Concatenation: `emb_sub[256] + v_stats[16] + cvec[100]` = **372-dim**
- Each component normalized separately before concatenation

### 3.2 FAISS Similarity Search

| Parameter | Value |
|-----------|-------|
| Index type | IndexFlatIP (inner product = cosine for L2-normalized vectors) |
| Vector dimension | 372 |
| Search time (verified) | ~16μs per query |
| Normalization | L2 normalization before indexing |
| Database | Versioned SQLite with schema migration |

### 3.3 Egyptian Demographic Verification

| Layer | Weight | Components |
|-------|--------|------------|
| Bio analysis | 60% | Keywords, location matching, slang detection, Arabic ratio |
| Post analysis | 40% | Batch keyword/slang/location analysis across posts |
| Fast-pass bonus | +0.5 | Location keyword match in bio |
| Agreement bonus | +0.15 | Multi-layer keyword match |
| Slang bonus | +0.2 | High slang density (>0.1) |
| **Threshold** | **0.7** | Scores ≥ 0.7 classified as Egyptian |

## 4. Dataset

| Attribute | Value |
|-----------|-------|
| Platform | Twitter/X |
| Accounts | 31 Egyptian Twitter accounts |
| Account types | Public figures, news outlets, activists, general users |
| Data format | Raw JSON files in `raw/` directory |
| Collection method | Manual curation + Selenium scraping |
| **Known limitation** | Convenience sample, no control group, no systematic selection |

## 5. All 15 Experiments

| # | Experiment | Hypothesis | Status | Result |
|---|-----------|------------|--------|--------|
| 1 | Stylometric fingerprint computation | 372-dim vectors can be produced from Arabic Twitter text | **PASS** | Vectors computed; 3-model ensemble operational |
| 2 | Multi-model ensemble load | MarBERT, AraBERT, MPNet all load successfully | **PARTIAL FAIL** | MarBERT/AraBERT fail with HuggingFace auth errors; falls back to MPNet only |
| 3 | Demographic filtering precision | EgyptianAccountVerifier correctly scores Egyptian accounts | **PASS** | All 31 accounts scored; verification pipeline functional |
| 4 | FAISS index construction | 372-dim vectors can be indexed with FAISS IndexFlatIP | **PASS** | Index built successfully; dimension consistency critical |
| 5 | FAISS search speed | Search completes in <100μs per query | **PASS** | ~16μs per query verified |
| 6 | FAISS dimension consistency | Pipeline and search use consistent dimensions | **FAIL** | Legacy (734-dim) vs. pipeline (372-dim) mismatch |
| 7 | Database versioning | Versioned fingerprint schema works | **PASS** | Schema with increment, confidence, diffs operational |
| 8 | Data ingestion from raw JSON | `ingest_from_raw.py` loads JSON files to DB | **PASS** | ETL pipeline functional |
| 9 | End-to-end pipeline | scrape → fingerprint → index → search chain works | **PARTIAL** | Broken at FAISS search due to dimension mismatch |
| 10 | Graph construction | GraphEngine builds directed graph from DB | **PASS** | Node/edge construction functional |
| 11 | Centrality computation | Degree, betweenness, eigenvector centrality compute | **PASS** | All three metrics computed |
| 12 | Coordination detection | Connected components clustering works | **PASS** | Clustering functional |
| 13 | Dashboard visualization | Django views render with data | **PASS** | 10 views operational |
| 14 | Report generation | Excel/HTML/Markdown output produced | **PASS** | All three formats working |
| 15 | System certification | `sovereign_certify.py` checks pass | **PASS** | Dependency, pipeline, directory, database audits pass |

### Results Summary

| Outcome | Count |
|---------|-------|
| **PASS** | 10 |
| **PARTIAL** | 2 |
| **FAIL** | 1 |
| **PARTIAL FAIL** | 1 |
| Not applicable (single-pass) | 1 |

## 6. Code Organization

```
Root/
├── AnubisX/
│   ├── shared/
│   │   ├── stylometry_core.py      # Core fingerprinting engine
│   │   ├── egyptian_verifier.py     # Demographic filtering
│   │   ├── config_base.py           # Knowledge base
│   │   ├── browser_profile_manager.py
│   │   ├── platform_base.py
│   │   └── utils.py
│   ├── twitter/
│   │   ├── adapter.py
│   │   ├── scrapers/
│   │   │   ├── session_manager.py
│   │   │   └── twitter_scraper_loggedin.py
│   │   └── vector/
│   │       └── pipeline.py
│   ├── facebook/
│   │   ├── adapter.py
│   │   └── scrapers/ (infrastructure only)
│   └── analysis/
│       └── graph_engine.py
├── UI/
│   └── anubis_x/
│       └── core/
│           ├── views.py
│           └── services.py
├── features.py                    # Legacy (734-dim)
├── extract_fp.py                  # v2.3 pipeline
├── extract_all_fingerprints.py    # Standalone extraction
├── build_fingerprints.py          # Legacy batch builder
├── faiss_build.py                 # Legacy index builder
├── faiss_search.py                # Legacy search
├── db_init.py                     # DB init
├── ingest_from_raw.py             # ETL
└── run_all.py                     # Orchestrator
```

**Metrics**: 47 Python files, 5 packages, ~2,800 total lines of code

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


