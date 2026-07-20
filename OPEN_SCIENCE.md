# Open Science Statement — AnubisX Framework

**Version:** 2.0.0 — Journal Research Edition  
**Date:** July 18, 2026  
*Classification: PUBLIC (C0)*

---

## Executive Summary

The AnubisX Framework is committed to the principles of open science: **transparency, reproducibility, accessibility, and collaboration**. This document serves as the formal open science statement, providing a comprehensive declaration of our research practices and commitments.

---

## Open Access

The AnubisX Framework adheres to the **Creative Commons Attribution 4.0 International (CC BY 4.0)** open access license, ensuring barrier-free access to all research outputs.

### License Terms

| Right | Granted |
|---|---|
| **Share** | Copy and redistribute in any medium or format |
| **Adapt** | Remix, transform, and build upon for any purpose |
| **Commercial use** | Permitted with attribution |

**Condition:** Attribution must be given to the original work with a link to the license and indication of changes. See [LICENSE.md](LICENSE.md) for complete terms.

### Open Access Compliance

- ✅ **Plan S Compliant** — Meets cOAlition S requirements
- ✅ **Institutional Repository Compatible** — Accepted by most academic institutions
- ✅ **Funder Mandate Compliant** — Meets most open access funding requirements
- ✅ **Wikimedia Compatible** — Compatible with Wikipedia redistribution

---

## Data Availability

### Current Data

| Type | Availability | Location |
|---|---|---|
| Experimental results (15 experiments) | Public | Repository: Anubis Twitter/reports/experimental_results/ |
| Twitter account data (31 accounts) | Public | Repository: Anubis Twitter/data/ |
| Experiment JSON outputs (17 files) | Public | Repository: Anubis Twitter/reports/experimental_results/ |

### Data Principles

1. **Public data only:** All experimental data is sourced from publicly available Twitter data
2. **Minimum necessary:** Data collection follows the minimum necessary principle
3. **Compliance:** All data collected in compliance with platform Terms of Service
4. **Anonymization:** No personally identifiable information beyond what is publicly available
5. **Provenance:** All data is traceable to its source

### Future Data Releases

Additional datasets collected for future experiments will be released under the same open access principles, subject to ethical and legal constraints.

---

## Code Availability

| Component | License | Location |
|---|---|---|
| Anubis Twitter v2.5 prototype | MIT | Repository |
| Feature extraction pipeline | MIT | Repository |
| FAISS similarity search | MIT | Repository |
| Experiment framework | MIT | Repository |

### Code Principles

1. All prototype code is open source
2. Code is accompanied by documentation
3. Dependencies are documented
4. Known limitations are transparently disclosed
5. Contributions are welcome via pull requests

---

## Reproducibility

### Current Reproducibility Status

- **Fully reproducible:** Cross-user similarity distribution, FAISS performance metrics, lexical feature analysis
- **Partially reproducible:** Fingerprint extraction (hash() non-determinism affects n-gram features)
- **Not reproducible (no data):** Temporal feature analysis, coordination detection, multi-modality experiments

### Reproducibility Requirements

| Requirement | Details |
|---|---|
| Software | Python 3.10+, FAISS, sentence-transformers, NumPy, scikit-learn, pandas |
| Hardware | CPU only (GPU optional) |
| Data | 31 JSON account files included |
| Time | ~5 minutes for full pipeline |
| Known issues | Python hash() non-determinism documented |

### Reproducibility Documentation

See manuscript Section 17 for complete reproducibility documentation.

---

## Citation Policy

### Preferred Citation

```bibtex
@software{anubisx2026framework,
  title = {AnubisX Framework: A Scientific Methodology for Behavioral Identity Attribution},
  author = {Awad, Ahmed},
  year = {2026},
  version = {2.0.0},
  url = {https://github.com/AnubisXFramework/AnubisXFramework},
  doi = {10.5281/zenodo.21446923},
  license = {CC-BY-4.0}
}
```

### Citation Metadata

Machine-readable citation metadata is available in [CITATION.cff](CITATION.cff).

### Citation Requirements

- All publications using the framework must cite the original work
- Derivative works must clearly indicate their relationship to the original
- Modifications and extensions must be documented

---

## Academic Reuse

### Permitted Uses

- Research and academic purposes
- Teaching and educational materials
- Derivative works with attribution
- Commercial applications with attribution

### Required Attribution

When using the framework in academic work, provide:

1. Citation to the DOI: [10.5281/zenodo.21446923](https://doi.org/10.5281/zenodo.21446923)
2. Reference to the repository: [https://github.com/AnubisXFramework/AnubisXFramework](https://github.com/AnubisXFramework/AnubisXFramework)
**Original Framework**: Ahmed Awad (NullC0d3)  
**Original Research**: Ahmed Awad (NullC0d3)  
3. License notice: CC BY 4.0

### Best Practices for Academic Reuse

1. Cite the framework and its foundational paper
2. Acknowledge limitations and uncertainties
3. Distinguish between framework components and your extensions
4. Share improvements and extensions with the community
5. Report issues and contribute fixes

---

## Licensing

| Component | License | Notes |
|---|---|---|
| Framework specification | CC BY 4.0 | Theoretical documentation |
| Prototype source code | MIT | Implementation code |
| Experimental data | CC BY 4.0 | Results and analysis |
| Figures and diagrams | CC BY 4.0 | Visual materials |
| Third-party content | Original licenses | Respective owners |

### License Compatibility

CC BY 4.0 is compatible with:
- Open access publication requirements
- Most institutional repository policies
- Funding body open access mandates (Plan S, etc.)
- Wikipedia and Wikimedia projects

---

## Open Science Badges

The framework supports the following open science practices eligible for badges:

| Practice | Status | Evidence |
|---|---|---|
| Open access | Yes | CC BY 4.0 license |
| Open data | Yes | Experimental data included |
| Open code | Yes | Prototype code included |
| Preregistration | Planned | Future experiments |
| Registered report | Planned | Future submissions |
| Reproducibility | Partial | Documented in Section 17 |

---

## Related Documents

| Document | Description |
|---|---|
| [README.md](README.md) | Main repository landing page |
| [ACADEMIC.md](ACADEMIC.md) | Academic profile and author information |
| [CITATIONS.md](CITATIONS.md) | Citation formats and examples |
| [PROJECT_IDENTIFIERS.md](PROJECT_IDENTIFIERS.md) | Centralized identifier reference |

---

**© 2026 Ahmed Awad (NullC0d3). All rights reserved.**  
*This document represents the official open science statement for the AnubisX Framework.*


