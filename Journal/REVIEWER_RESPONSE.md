# Reviewer Response — AnubisX Framework v2.0 Journal Revision

**Date:** July 16, 2026  
**Author:** Ahmed Awad (NullC0d3)  
*Classification: PUBLIC (C0)*

---

## Overview

This document addresses 14 reviewer concerns identified during the v1.0 → v2.0 journal revision process. All concerns have been addressed in the current manuscript.

---

## Concern Resolution

| # | Concern | v1.0 Status | v2.0 Resolution |
|---|---|---|---|
| 1 | Reference completeness | 19 references (17 self-citations) | Expanded to 50 references (31 external peer-reviewed, 19 self-citations); external ratio 62% |
| 2 | Claims validation status | Claims presented without validation status | All 10 core claims classified: 6 PUBLICATION READY, 1 DEGRADED, 3 REQUIRES DATA (Table 11) |
| 3 | Data provenance | Results presented without source traceability | All experiment values reference raw JSON output files (EXP-001 through EXP-015) |
| 4 | Self-citation ratio | 89% self-citations | Reduced to 38% self-citations; 62% external peer-reviewed references |
| 5 | Mathematical depth | Minimal mathematical exposition | Expanded to 292 objects across 24 categories, 50 equations, 47 functions, 10 formal spaces |
| 6 | Implementation availability | Theoretical specification only | Full prototype code (47 Python files, ~2,800 LOC) available in repository |
| 7 | Reproducibility | No reproducibility section | New dedicated Section 17 with dependencies, dataset, and reproducibility notes |
| 8 | Ethics and dual-use | Brief ethics statement | Strengthened with explicit dual-use acknowledgment and responsible use framework |
| 9 | Theory-empiricism gap | 42% gap not addressed | Gap explicitly documented with transparent status for each framework component |
| 10 | Related work depth | 6 subsections | Expanded to 11 subsections with comparative analysis table (Table 1) |
| 11 | Limitations structure | Unstructured limitations | All 10 prototype limitations documented with severity, impact, and mitigation pathways (Table 12) |
| 12 | Multi-modality status | Unclear implementation status | Clear validation status table for each modality (Table 6: 1 validated, 4 require data) |
| 13 | Comparison to baselines | No baseline comparison | Qualitative comparison table (Table 1) with 5 dimensions across 5 approaches |
| 14 | Publication venue suitability | No target venues | 4 target venues identified with scope match and priority ranking |

---

## Detailed Responses

### Concern 1: Reference Completeness

**Resolution:** References expanded from 19 to 50. External peer-reviewed references from IEEE (3), ACM (4), Elsevier (6), Springer (5), ACL (5), CEUR-WS (3), arXiv (4), and Books (3). Self-citation ratio reduced from 89% to 38%.

### Concern 2: Claims Validation

**Resolution:** All 10 core empirical claims are now classified with explicit validation status: 6 claims at PUBLICATION READY, 1 at DEGRADED, 3 at REQUIRES DATA. Each claim is supported by evidence from raw JSON experiment output.

### Concern 3: Data Provenance

**Resolution:** Every experimental value in the manuscript is traceable to its source JSON file (EXP-001 through EXP-015). No fabricated or extrapolated values.

### Concern 4: Self-Citation Ratio

**Resolution:** The self-citation ratio (repository documentation references to external peer-reviewed references) has been reduced from 89% (v1.0) to 38% (v2.0), achieved by adding 31 new external references across 12 research domains.

### Concern 5: Mathematical Depth

**Resolution:** The mathematical framework section (Section 7) now documents 292 objects across 24 categories, 6 layers, 10 formal spaces, 9 distance functions, 7 similarity functions, and the complete likelihood ratio evidence framework.

### Concern 6: Implementation Availability

**Resolution:** The prototype implementation (Anubis Twitter v2.5, 47 Python files, ~2,800 LOC) is included in the repository under MIT license. Section 9 documents the implementation architecture.

### Concern 7: Reproducibility

**Resolution:** New Section 17 provides complete reproducibility information including software dependencies, dataset location, known reproducibility limitations (hash() non-determinism), and framework documentation references.

### Concern 8: Ethics and Dual-Use

**Resolution:** The ethics statement now explicitly acknowledges dual-use potential, advocates responsible use within legal and ethical frameworks, and emphasizes the importance of public scrutiny through open-source release.

### Concern 9: Theory-Empiricism Gap

**Resolution:** The 42% theory-implementation gap is explicitly documented. The manuscript clearly distinguishes between the complete theoretical specification and the partial prototype implementation. Formal experiments (38) are clearly marked as DEFINED/unexecuted.

### Concern 10: Related Work Depth

**Resolution:** Related Work expanded from 6 to 11 subsections covering authorship attribution, stylometry, digital forensics, CTI, behavioral biometrics, OSINT, and Identity Intelligence. New comparative analysis (Table 1) positions the framework against existing approaches across 5 dimensions.

### Concern 11: Limitations Structure

**Resolution:** All 10 prototype limitations are documented with severity (Critical/Major/Minor), impact assessment, and specific mitigation pathways (Table 12). Framework-level limitations and generalizability constraints are addressed separately.

### Concern 12: Multi-Modality Status

**Resolution:** Table 6 clearly shows validation status for all five modalities: Stylometry (Validated), Chrono-Profiling (Requires Data), Terminal Profiling (Requires Data), Network Analysis (Requires Data), Media Forensics (Requires Data).

### Concern 13: Comparison to Baselines

**Resolution:** Table 1 provides qualitative comparison across 5 approaches (Stylometry, Behavioral Biometrics, CTI Attribution, Digital Forensics, AnubisX) on 6 dimensions (multi-modal scope, formal theory, mathematical framework, pre-specified criteria, validated prototype, open science).

### Concern 14: Publication Venue Suitability

**Resolution:** Four target venues identified: Journal of Cybersecurity and Privacy (MDPI), Electronics (MDPI), SN Computer Science (Springer), Frontiers in Computer Science. Each assessed for scope match and priority.

---

## Summary

All 14 reviewer concerns have been resolved in the v2.0 Journal Revision. The manuscript is assessed at **8.5/10** readiness with remaining improvements limited to figure generation and final proofreading.

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


