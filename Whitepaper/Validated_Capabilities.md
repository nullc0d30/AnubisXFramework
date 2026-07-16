# Validated Capabilities

**AnubisX Framework — Empirically Verified Functionality**

---

**Document ID**: WHP-011  
**Version**: 1.0  
**Owner**: Ahmed Awad (NullC0d3)  
**Status**: ESTABLISHED  
**Dependencies**: WHP-009, WHP-010  
**Referenced Documents**: Prototype.md, Experimental_Validation.md  
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

## 1. Overview

This document catalogs the capabilities of the Anubis Twitter Intelligence Prototype v2.5 that have been empirically validated through static code analysis and/or execution. Each capability is assessed with verification status, operational conditions, and limitations.

## 2. Capability Inventory

### C01: Stylometric Fingerprint Generation

| Field | Value |
|-------|-------|
| **Status** | **VERIFIED** |
| Evidence | `stylometry_core.py:59-181` — 3-model ensemble → 372-dim fingerprint |
| Code Details | 256-dim multilingual embedding + 16-dim numerical stats + 100-dim character hash |
| Conditions | sentence-transformers, torch; model downloads from HuggingFace (~2GB) |
| Limitations | MarBERT/AraBERT fail with HuggingFace auth errors; silent fallback to single MPNet degrades ensemble |

### C02: Egyptian Demographic Verification

| Field | Value |
|-------|-------|
| **Status** | **VERIFIED** |
| Evidence | `egyptian_verifier.py:17-78` — `calculate_egypt_score()` method |
| Code Details | 3-layer scoring (bio 60%, posts 40%), 3 bonus mechanisms, 200+ cultural indicators |
| Conditions | Python `re` module only. No ML models required. |
| Limitations | Threshold (0.7) hardcoded and unvalidated. Knowledge base covers only Egyptian Arabic. Bonuses can push scores beyond meaningful calibration. |

### C03: SQLite Versioned Storage

| Field | Value |
|-------|-------|
| **Status** | **VERIFIED** |
| Evidence | `pipeline.py:29-64` — versioned fingerprints schema with migration |
| Code Details | Schema: id, username, fingerprint_version, fingerprint_vec, confidence, diff, created_at |
| Conditions | Python sqlite3 (stdlib). Write permissions. |
| Limitations | 4+ distinct database schemas across codebase. No unified access layer. No migration tool. |

### C04: FAISS Similarity Search

| Field | Value |
|-------|-------|
| **Status** | **VERIFIED (with caveats)** |
| Evidence | `pipeline.py:174-208` — IndexFlatIP, L2 normalization, ~16μs query time |
| Code Details | 372-dim vectors, cosine similarity via inner product, top-k retrieval |
| Conditions | faiss library, numpy. Dimension must match between build and search. |
| Limitations | **Critical**: Pipeline uses 372-dim; legacy scripts use 734-dim. Dimension mismatch causes `faissException`. Cross-script search is broken. |

### C05: Twitter Web Scraping

| Field | Value |
|-------|-------|
| **Status** | **PARTIALLY VERIFIED** |
| Evidence | `twitter_scraper_loggedin.py:32-133` |
| Code Details | Profile scraping with bio extraction, tweet scrolling, session management |
| Conditions | Chrome/chromedriver, selenium, valid Twitter/X session, manual login |
| Limitations | **No timestamp capture** — all tweets get `datetime.now()`. Manual login required. No historical pagination. CSS selectors fragile. |

### C06: Graph / Network Analysis

| Field | Value |
|-------|-------|
| **Status** | **IMPLEMENTED (untested with real data)** |
| Evidence | `graph_engine.py:18-186` — directed graph, centrality, coordination |
| Code Details | Degree, betweenness, eigenvector centrality. Connected components clustering. |
| Conditions | networkx, numpy, populated DB, raw JSON files for edge extraction |
| Limitations | Mention extraction is simplistic (space-split). No Louvain/Leiden. Betweenness k=100 sampling may miss nodes. No visualization. |

### C07: Dashboard / UI Visualization

| Field | Value |
|-------|-------|
| **Status** | **VERIFIED** |
| Evidence | `views.py:1-70` — 10 Django views; `services.py:1-216` — AnubisBackend |
| Code Details | dashboard, search, user_detail, analytics, api_search, api_user, api_compare, api_graph |
| Conditions | Django, populated SQLite databases |
| Limitations | Backend returns empty if no fingerprints. Threat detection is mock (simple threshold). System health uses hardcoded fallback values. |

### C08: Document / Report Generation

| Field | Value |
|-------|-------|
| **Status** | **VERIFIED** |
| Evidence | `view_analytics.py:67-225` — Excel/HTML reports; `export_fingerprints.py:9-82` — Markdown |
| Code Details | Excel with auto-filters, HTML with Bootstrap/DataTables, Markdown fingerprint summaries |
| Conditions | openpyxl for Excel. Populated database. |
| Limitations | Reports from specific databases only (fingerprints1.db). Hardcoded output paths. No unified cross-DB reporting. |

### C09: System Certification / Audit

| Field | Value |
|-------|-------|
| **Status** | **VERIFIED** |
| Evidence | `sovereign_certify.py:8-59`, `red_team_audit.py:12-67`, `verify_status.py:9-47` |
| Code Details | Python version check, dependency import check, pipeline smoke test, directory/database audit |
| Limitations | Checks Python version and imports only. Does not verify model integrity, data consistency, or security posture. |

## 3. Not Yet Validated

| Capability | Status | Reason |
|-----------|--------|--------|
| Cross-platform identity matching | NOT IMPLEMENTED | Twitter/Facebook pipelines run independently; no vector comparison |
| Facebook data collection | NOT IMPLEMENTED | Adapter/scraper infrastructure exists but never executed |
| Deception / style shift detection | NOT IN v2.5 | Only in legacy `extract_fp.py` |
| Temporal feature analysis | DATA-DEPENDENT | Scraper does not capture timestamps; requires pre-collected data |
| Multi-modal fusion | NOT IMPLEMENTED | Only stylometry modality operational |

## 4. Operational Scenarios

### Offline Analysis (Recommended)
1. Collect Twitter data via external tools (with timestamps)
2. Format as JSON array with `content` and `created_at` fields
3. Place in `raw/` directory
4. Run fingerprint pipeline (no login needed)
5. Analyze with reports or dashboard

### Live Monitoring (Manual)
1. Run `python -m AnubisX.twitter.run_all`
2. Perform manual login in browser
3. Script scrapes hardcoded targets → fingerprints → searches → graphs
4. Results stored in `twitter.db` / `twitter.index`

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
