# Publication Change Log — AnubisX Framework

## v2.0 — Journal Revision (July 16, 2026)

### Major Changes from v1.1

#### Structural Changes
- Added **Section 13: Practical Implications** (4 subsections: cybersecurity, digital forensics, intelligence analysis, open-source research)
- Added **Section 16: Summary of Contributions** (theoretical, methodological, empirical)
- Added **Section 17: Reproducibility** (dedicated reproducibility section)
- Renumbered sections 13→14, 14→15, 15→18
- Expanded Related Work from 6 to 11 subsections (added 3.6 Comparative Analysis with Table 1)
- Expanded Discussion from 4 to 6 subsections (added 12.4 Cybersecurity/Forensics, 12.5 OSINT/Intelligence)

#### Reference Improvements
- **Total references:** 19 → 50 (+31 new)
- **External peer-reviewed references:** 2 → 31
- **Self-citation ratio:** 89% → 38%
- **New reference domains:**
  - PAN/CLEF workshop series (6 new: [22]-[25])
  - Transformer/SBERT embeddings (1 new: [26])
  - Arabic NLP (3 new: [27]-[29])
  - Cyber threat attribution surveys (3 new: [1], [2], [35])
  - LLM-based attribution (1 new: [36])
  - Behavioral biometrics (3 new: [38]-[40])
  - Forensic linguistics (2 new: [30], [31])
  - FAISS (1 new: [43])
  - Statistical evidence evaluation (1 new: [45])
  - Survey papers (3 new: [47]-[50])
- All "Citation Required" placeholders replaced with real citations

#### Tables Added/Expanded
- **Table 1:** Comparative analysis of AnubisX vs existing approaches (NEW)
- **Table 12:** Prototype limitations with mitigation pathways (expanded from 10 to 10+mitigation rows)
- All tables renumbered and cross-referenced

#### Figure Placeholders
- **Fig. 1:** Authorship Attribution Research Timeline
- **Fig. 2:** AnubisX Framework Architecture
- **Fig. 3:** Stylometric Fingerprint Extraction Pipeline
- **Fig. 4:** Cross-User Cosine Similarity Distribution
- **Fig. 5:** Operational Deployment Scenarios
- **Fig. 6:** Research and Development Roadmap

#### Content Enhancements
- Expanded Threats to Validity from 4 to 6 types (added ecological, temporal)
- Added mitigation pathways to all 10 prototype limitations
- Added section on FAISS scalability context (billion-scale design vs 31-vector use case)
- Added discussion of embedding dominance and topic confound in similarity results
- Strengthened ethics and dual-use discussion
- Enhanced acknowledgements with specific library versions

#### Data Corrections Maintained (from v1.1)
- Cross-user similarity mean: 0.26 → 0.697 (from EXP-002 JSON)
- Keyword matches: 5,127 → 144 (from EXP-015 JSON)
- FAISS latency: 16 µs → 6–8 µs (from EXP-006 JSON)
- TTR values: raw experimental values with inflation caveat retained
- Temporal features: corrected to show partial data availability (not absent)

### Files
- `AnubisX_Framework_Foundational_Paper_v2.0.docx` — Journal-ready manuscript (62 KB, 18 sections, 12 tables, 50 references)
- `PUBLICATION_READINESS_REPORT.md` — Readiness assessment (8.5/10)
- `PUBLICATION_CHANGE_LOG.md` — This file

---

**Project**: AnubisX Framework  
**Primary Author**: Ahmed Awad (NullC0d3)  
**Author Profile**: https://www.linkedin.com/in/nullc0d3/  
**Original Framework**: Ahmed Awad (NullC0d3)  
**Original Research**: Ahmed Awad (NullC0d3)  
**Repository**: Official AnubisX Repository  

**Copyright** © 2026 Ahmed Awad (NullC0d3). All rights reserved.  
Original documentation, framework design, algorithms, source code, diagrams, and repository structure are the intellectual work of Ahmed Awad (NullC0d3), unless otherwise indicated. Third-party software, libraries, datasets, and referenced works remain the property of their respective owners and are governed by their own licenses.

**DOI**: https://doi.org/10.5281/zenodo.21393392

---

*Classification: PUBLIC (C0)*
