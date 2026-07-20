# Tables — AnubisX Framework

**Publication-Ready Table Specifications**

**Date:** July 16, 2026  
*Classification: PUBLIC (C0)*

---

This directory documents all 12 tables used by the AnubisX Framework foundational paper (v2.0). Each entry explains the purpose, data source, and manuscript section reference.

---

## Table Inventory

### Table 1: Comparative Analysis of AnubisX vs Existing Approaches

**Purpose:** Qualitative comparison of the AnubisX Framework against existing approaches across key dimensions.

**Source:** Author analysis based on literature review (Section 3)

**Manuscript Section:** Section 3.6

**Dimensions (5 approaches x 6 criteria):**
- Approaches: Stylometry, Behavioral Biometrics, CTI Attribution, Digital Forensics, AnubisX
- Criteria: Multi-modal scope, Formal theory, Mathematical framework, Pre-specified criteria, Validated prototype, Open science

**Data:** Qualitative assessment (Yes/No/Partial/Limited with annotations)

---

### Table 2: Axiom Groups, Counts, and Scope

**Purpose:** Summary of the 16 formal axioms organized into six groups.

**Source:** Axiomatic system documentation (Axioms/Core_Axioms.md)

**Manuscript Section:** Section 6.1

**Content:** 6 groups: Core (4), Behavior (3), Identity (2), Attribution (2), Evidence (3), Reasoning (2)

---

### Table 3: Mathematical Framework Layers with Object Counts

**Purpose:** Overview of the 292 mathematical objects organized into six layers.

**Source:** Mathematical framework documentation (Mathematics/Mathematical_Foundation.md)

**Manuscript Section:** Section 7

**Layers:** Foundation Types (39), Structured Types (26), Transformations (31), Comparison & Evaluation (26), Uncertainty & Decision (32), Constraint & Optimization (15)

---

### Table 4: Likelihood Ratio Verbal Interpretation Scale

**Purpose:** Standardized verbal interpretation scale for likelihood ratio values.

**Source:** LR framework documentation (Mathematics/Equations/EQ-017)

**Manuscript Section:** Section 7.2

**Ranges:** >100 (Very strong), 10-100 (Strong), 3-10 (Moderate), 1-3 (Limited), 1 (No support), and corresponding ranges for different-source support

---

### Table 5: Six-Layer Architecture

**Purpose:** Summary of the six-layer architecture with layer responsibilities and key functions.

**Source:** Architecture documentation (Framework/Framework_Architecture.md)

**Manuscript Section:** Section 8.1

**Content:** Data Layer, Feature Layer, Profile Layer, Comparison Layer, Evidence Layer, Decision Layer

---

### Table 6: Five Behavioral Modalities

**Purpose:** Overview of the five behavioral modalities with algorithms and validation status.

**Source:** Framework module documentation (Framework/Framework_Modules.md)

**Manuscript Section:** Section 8.3

**Modalities:** Stylometric (Validated), Chrono-Profiling (Requires data), Terminal Profiling (Requires data), Network Analysis (Requires data), Media Forensics (Requires data)

---

### Table 7: Cross-User Cosine Similarity Distribution

**Purpose:** Distribution of cosine similarity values across 465 cross-user identity pairs.

**Source:** EXP-002 JSON experimental results

**Manuscript Section:** Section 11.2

**Metrics:** Mean (0.697), Std dev (0.105), Min (0.377), Max (0.974), Pairs by threshold

---

### Table 8: FAISS Index Performance Metrics

**Purpose:** Performance metrics for the FAISS similarity search index.

**Source:** EXP-006 JSON experimental results

**Manuscript Section:** Section 11.3

**Metrics:** Index type, Vectors (31 x 372), File size (46,173 B), Read time (0.0004 s), Mean latency (6-8 µs)

---

### Table 9: Lexical Feature Distribution

**Purpose:** Distribution of lexical features across 31 users with TTR inflation caveat.

**Source:** EXP-004 JSON experimental results

**Manuscript Section:** Section 11.4

**Features:** TTR, Avg word length, Punctuation ratio, Emoji ratio (with mean, std, min, max)

**Note:** TTR inflated by accounts with <5 tweets (r ≈ -0.72 with tweet count)

---

### Table 10: Egyptian Content Verification Results

**Purpose:** Results of Egyptian linguistic content verification.

**Source:** EXP-015 JSON experimental results

**Manuscript Section:** Section 11.7

**Metrics:** Keyword matches (144), Slang matches (58), Location mentions (12)

---

### Table 11: Claims Validation Summary

**Purpose:** Validation status for 10 core empirical claims.

**Source:** Aggregate analysis of all 15 experiments

**Manuscript Section:** Section 11.8

**Status categories:** PUBLICATION READY (6), DEGRADED (1), REQUIRES DATA (3)

---

### Table 12: Prototype Limitations with Mitigation Pathways

**Purpose:** Comprehensive documentation of prototype limitations with severity ratings and mitigation strategies.

**Source:** Prototype documentation and experimental analysis

**Manuscript Section:** Section 14.1

**Limitations:** 10 items with ID, description, severity (Critical/Major/Minor), and mitigation pathway

---

## Data Source Reference

| Table | Primary Source | Location |
|---|---|---|
| 1 | Literature review | Section 3 |
| 2 | Axioms/Core_Axioms.md | Repository |
| 3 | Mathematics/Mathematical_Foundation.md | Repository |
| 4 | Mathematics/Equations/EQ-017 | Repository |
| 5 | Framework/Framework_Architecture.md | Repository |
| 6 | Framework/Framework_Modules.md | Repository |
| 7 | EXP-002.json | Anubis Twitter/reports/ |
| 8 | EXP-006.json | Anubis Twitter/reports/ |
| 9 | EXP-004.json | Anubis Twitter/reports/ |
| 10 | EXP-015.json | Anubis Twitter/reports/ |
| 11 | All experiments | Aggregate |
| 12 | Prototype analysis | Author assessment |

---

**Project**: AnubisX Framework  
**Primary Author**: Ahmed Awad (NullC0d3)  
**Author Profile**: https://www.linkedin.com/in/nullc0d3/  
**ORCID**: https://orcid.org/0009-0005-0654-3393  
**Repository**: [https://github.com/AnubisXFramework/AnubisXFramework](https://github.com/AnubisXFramework/AnubisXFramework)  
**Original Framework**: Ahmed Awad (NullC0d3)  
**Original Research**: Ahmed Awad (NullC0d3)  
**DOI**: [https://doi.org/10.5281/zenodo.21446923](https://doi.org/10.5281/zenodo.21446923)

**Copyright** © 2026 Ahmed Awad (NullC0d3). All rights reserved.
Original documentation, framework design, algorithms, source code, diagrams, and repository structure are the intellectual work of Ahmed Awad (NullC0d3), unless otherwise indicated. Third-party software, libraries, datasets, and referenced works remain the property of their respective owners and are governed by their own licenses.


*Classification: PUBLIC (C0)*


