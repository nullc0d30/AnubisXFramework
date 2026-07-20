<p align="center">
  <img src="logo.png" alt="AnubisX Framework Logo" width="200"/>
</p>

# AnubisX Framework

**A Scientific Methodology for Behavioral Identity Attribution**

[![DOI](https://img.shields.io/badge/DOI-10.5281/zenodo.21446923-blue)](https://doi.org/10.5281/zenodo.21446923)
[![Version](https://img.shields.io/badge/Version-3.0.0--Scientific%20Re%20Architecture-brightgreen)](RELEASE_NOTES_v3.0.md)
[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)
[![GitHub Release](https://img.shields.io/badge/GitHub-Release-blueviolet)](https://github.com/AnubisXFramework/AnubisXFramework/releases)
[![Status: Theoretical + Prototype](https://img.shields.io/badge/Status-Theoretical%20%2B%20Prototype-blue)](ROADMAP_v2.md)
[![Publication Status](https://img.shields.io/badge/Publication-Journal%20Ready-success)](PUBLICATION_STATUS.md)
[![Python](https://img.shields.io/badge/Python-3.10%2B-blue)](https://www.python.org/)
[![Research](https://img.shields.io/badge/Research-Open%20Science-orange)](OPEN_SCIENCE.md)
[![Open Science](https://img.shields.io/badge/Open%20Science-CC%20BY%204.0-green)](https://creativecommons.org/licenses/by/4.0/)

---

## Research Identity

The AnubisX Framework is a formal scientific methodology for determining the identity of a human operator from their digital behavioral patterns. Unlike traditional attribution methods that rely on transient technical artifacts — IP addresses, device fingerprints, browser configurations — the framework measures **persistent human cognitive signatures** that are rooted in stable cognitive processing habits.

**DOI:** [10.5281/zenodo.21446923](https://doi.org/10.5281/zenodo.21446923)  
**Repository:** [https://github.com/AnubisXFramework/AnubisXFramework](https://github.com/AnubisXFramework/AnubisXFramework)

[**ACADEMIC_PROFILE**](ACADEMIC.md) | [**PUBLICATIONS**](PUBLICATIONS.md) | [**RESEARCH_NETWORK**](RESEARCH_NETWORK.md) | [**CITATIONS**](CITATIONS.md) | [**PROJECT_IDENTIFIERS**](PROJECT_IDENTIFIERS.md)

**Original Framework**: Ahmed Awad (NullC0d3)  
**Original Research**: Ahmed Awad (NullC0d3)

---

## Research Motivation

Digital attribution — linking digital actions to their human source — is a foundational capability in cyber threat intelligence, digital forensics, and national security. Current methodologies rely primarily on technical artifacts that sophisticated adversaries can spoof or eliminate. Behavioral attribution offers an alternative paradigm: analyzing intrinsic patterns of human cognition observable through digital traces.

The framework addresses three specific limitations:
1. **Fragmentation** — Behavioral attribution methods are developed independently across disciplines without unifying theory
2. **Methodological rigor** — Most work lacks formal, pre-specified validation criteria
3. **Transparency** — Comprehensive documentation of limitations and failure modes is uncommon

---

## Repository Overview

| Directory | Contents |
|---|---|
| `Journal/` | Journal revision materials, publication documents, submission checklists |
| `Documentation/` | Comprehensive public documentation (12 files) |
| `Theory/` | Theoretical foundation documents |
| `Framework/` | Architecture, workflow, modules, pipeline specifications |
| `Algorithms/` | Algorithm specifications |
| `Mathematics/` | Mathematical foundation, equations, functions |
| `Validation/` | Validation framework, acceptance criteria, metrics |
| `Research/` | Research methodology, questions, limitations |
| `Whitepaper/` | Complete whitepaper (15 documents) |
| `Release/` | Release notes, checklists, version documentation |
| `Citation/` | Citation metadata, format guides |
| `Provenance/` | Data provenance and chain-of-custody documentation |
| `Figures/` | Figure specifications for publications |
| `Tables/` | Table specifications for publications |
| `Examples/` | Implementation examples and walkthroughs |
| `API_Docs/` | API documentation and reference guides |
| `Data/` | Dataset specifications and references |
| `Scripts/` | Utility scripts and automation tools |
| `FAQ/` | Frequently asked questions |
| `Getting_Started/` | Step-by-step orientation guides |

---

## Framework Architecture

```
┌────────────────────────────────────────────────────────────┐
│                   Decision Layer                            │
├────────────────────────────────────────────────────────────┤
│                   Evidence Layer                            │
├────────────────────────────────────────────────────────────┤
│                  Comparison Layer                           │
├────────────────────────────────────────────────────────────┤
│                  Profile Layer                              │
├────────────────────────────────────────────────────────────┤
│                  Feature Layer                              │
├────────────────────────────────────────────────────────────┤
│                    Data Layer                               │
└────────────────────────────────────────────────────────────┘
```

### Six-Stage Pipeline

```
Ingestion → Feature Extraction → Profile Construction → Comparison → Evidence Evaluation → Decision
```

### Three Workflows

- **Identification (1:N)** — Determine who produced questioned material
- **Verification (1:1)** — Confirm or refute a claimed identity
- **Forensic Comparison (1:1)** — Compute likelihood ratio with evidence grading

### Five Behavioral Modalities

| Modality | Behavioral Signal | Validation Status |
|---|---|---|
| Forensic Stylometry | Vocabulary, syntax, discourse | Validated (prototype) |
| Chrono-Profiling | Circadian rhythms, timing patterns | Requires data |
| Terminal Execution Profiling | Commands, navigation patterns | Requires data |
| Relational Network Analysis | Graph structure, communities | Requires data |
| Environmental Media Forensics | File structure, naming conventions | Requires data |

---

## Prototype Status

**Anubis Twitter v2.5** — A working implementation of the stylometric modality for Arabic Twitter data:

- 47 Python source files, ~2,800 LOC
- 372-dimensional stylometric fingerprint extraction
- FAISS-based similarity search at 6–8 µs latency
- 15 executed experiments on 31 Egyptian Twitter accounts
- 6/10 empirical claims at **PUBLICATION READY** status

---

## Validation Status

| Component | Status |
|---|---|
| Axiomatic foundation | Complete (16 axioms) |
| Mathematical framework | Complete (292 objects, 50 equations) |
| Algorithm specifications | Complete (37 algorithms) |
| Validation framework | Complete (31 acceptance thresholds) |
| Benchmark framework | Complete (24 benchmarks) |
| Experiment designs | Complete (38 experiments — 15 executed) |
| Case studies | Complete (20 case studies) |
| Prototype implementation | Validated (stylometric fingerprinting, FAISS search) |
| Empirical validation | Partial — 6/10 publication-ready claims |
| Full software implementation | Next phase |

---

## Repository Timeline

| Year | Milestone |
|---|---|
| 2023 | Axiomatic foundation, initial framework design |
| 2024 | Whitepaper completion, Anubis Twitter v2.0 release, Reference book publication |
| 2025 | Prototype v2.5 validation, 15 experiments on Egyptian Twitter data |
| 2026 | Journal revision v2.0, Zenodo DOI assigned, publication preparation |

---

## Persistent Identifiers

| Platform | Identifier |
|---|---|
| **DOI** | [10.5281/zenodo.21446923](https://doi.org/10.5281/zenodo.21446923) |
| **ORCID** | [0009-0005-0654-3393](https://orcid.org/0009-0005-0654-3393) |
| **GitHub** | [nullc0d30/AnubisXFramework](https://github.com/AnubisXFramework/AnubisXFramework) |
| **See also:** | [PROJECT_IDENTIFIERS.md](PROJECT_IDENTIFIERS.md) |

---

## Research Citation Network

The framework is integrated into academic infrastructure through:

```
GitHub → Zenodo → OSF → ResearchGate → Figshare → SSRN → Journal Publication → Google Scholar → Crossref → OpenAlex
```

See [RESEARCH_NETWORK.md](RESEARCH_NETWORK.md) for the complete ecosystem visualization.

---

## Research Resources

| Resource | Link |
|---|---|
| **GitHub Repository** | [https://github.com/AnubisXFramework/AnubisXFramework](https://github.com/AnubisXFramework/AnubisXFramework) |
| **Zenodo Archive** | [https://doi.org/10.5281/zenodo.21446923](https://doi.org/10.5281/zenodo.21446923) |
| **ORCID** | [https://orcid.org/0009-0005-0654-3393](https://orcid.org/0009-0005-0654-3393) |
| **LinkedIn** | [https://www.linkedin.com/in/nullc0d3/](https://www.linkedin.com/in/nullc0d3/) |
| **ResearchGate** | [Profile](https://www.researchgate.net/profile/Ahmed-Awad-118) |
| **Reference Book** | [You Can Hide Your Name... Not Your Mind](https://www.amazon.com/dp/B0H8LCTTWW) |

---

## Publication History

| Publication | Status | Link |
|---|---|---|
| Foundational Paper (v2.0) | Journal-ready | [PUBLICATIONS.md](PUBLICATIONS.md) |
| Whitepaper | Complete | [Whitepaper/](Whitepaper/) |
| Reference Book (2024) | Published | [Amazon B0H8LCTTWW](https://www.amazon.com/dp/B0H8LCTTWW) |

---

## Open Science

The AnubisX Framework is committed to open science principles:

- ✅ **Open Access** — CC BY 4.0 license for all materials
- ✅ **Reproducibility** — Complete experimental pipeline documented
- ✅ **Transparency** — All limitations and failure modes disclosed
- ✅ **Data Availability** — 15 experiments with full results provided
- ✅ **Software Availability** — Prototype implementation included
- ✅ **Long-term Preservation** — Zenodo archival with DOI

See [OPEN_SCIENCE.md](OPEN_SCIENCE.md) for the complete open science statement.

---

## How to Cite

If you use the AnubisX Framework in your research, please cite:

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

Full citation examples in [CITATIONS.md](CITATIONS.md).

---

## Academic Profiles

| Platform | Profile |
|---|---|
| ORCID | [0009-0005-0654-3393](https://orcid.org/0009-0005-0654-3393) |
| LinkedIn | [/in/nullc0d3](https://www.linkedin.com/in/nullc0d3/) |
| ResearchGate | [/profile/Ahmed-Awad-118](https://www.researchgate.net/profile/Ahmed-Awad-118) |
| Figshare | [/authors/Ahmed_Awad/24415733](https://figshare.com/authors/Ahmed_Awad/24415733) |

---

## Repository Preservation

- **Primary Archive:** [Zenodo DOI 10.5281/zenodo.21446923](https://doi.org/10.5281/zenodo.21446923)
- **Secondary Archives:** GitHub, OSF (planned), Figshare
- **Citation Metadata:** [CITATION.cff](CITATION.cff)
- **Preservation Policy:** See [ACADEMIC.md](ACADEMIC.md)

---

## Scientific Contribution

The framework advances behavioral identity attribution through:

1. **Theoretical Innovation** — First comprehensive axiomatic foundation (16 axioms, 20 hypotheses, 18 design principles)
2. **Methodological Rigor** — Formal validation with 31 acceptance thresholds
3. **Technical Implementation** — Working prototype with FAISS similarity search
4. **Empirical Evidence** — Validated on 31 real-world Twitter accounts

---

## Future Research

- Additional behavioral modality implementations
- Coordinated network analysis
- Temporal profiling capabilities
- Multi-modal inference engine
- Peer-reviewed journal publication

See [ROADMAP_v2.md](ROADMAP_v2.md) for detailed roadmap.

---

## Getting Started

| Audience | Recommended Path |
|---|---|
| **Newcomers** | [Getting_Started/](Getting_Started/) → [FAQ/](FAQ/) → [Documentation/Theory_Guide.md](Documentation/Theory_Guide.md) |
| **Researchers** | [Documentation/Theory_Guide.md](Documentation/Theory_Guide.md) → [Documentation/Algorithms.md](Documentation/Algorithms.md) → [Documentation/Validation.md](Documentation/Validation.md) |
| **Developers** | [Documentation/Architecture.md](Documentation/Architecture.md) → [Documentation/Framework_Guide.md](Documentation/Framework_Guide.md) → [API_Docs/](API_Docs/) |
| **Forensic Practitioners** | [Documentation/Framework_Guide.md](Documentation/Framework_Guide.md) → [Documentation/Examples.md](Documentation/Examples.md) → [Documentation/Validation.md](Documentation/Validation.md) |

---

## Documentation

| Document | Description |
|---|---|
| [Overview](Documentation/Overview.md) | Complete framework introduction |
| [Getting Started](Getting_Started/) | Step-by-step orientation |
| [Framework Guide](Documentation/Framework_Guide.md) | Comprehensive framework reference |
| [Theory Guide](Documentation/Theory_Guide.md) | Theoretical foundations |
| [Architecture](ARCHITECTURE.md) | System architecture and component design |
| [Algorithms](Documentation/Algorithms.md) | Complete algorithm catalog |
| [Validation](Documentation/Validation.md) | Validation methodology and status |
| [FAQ](FAQ/) | Frequently asked questions |
| [Glossary](Documentation/Glossary.md) | Standardized terminology |
| [Examples](Documentation/Examples.md) | Case study walkthroughs |
| [References](Documentation/References.md) | Source document index |

---

## Related Publications

| Publication | Link |
|---|---|
| Foundational Paper | [Journal/AnubisX_Framework_Foundational_Paper_v2.0.md](Journal/AnubisX_Framework_Foundational_Paper_v2.0.md) |
| Whitepaper | [Whitepaper/AnubisX_Whitepaper.md](Whitepaper/AnubisX_Whitepaper.md) |
| Reference Book | [You Can Hide Your Name... Not Your Mind](https://www.amazon.com/dp/B0H8LCTTWW) |

---

## Acknowledgements

See [ACKNOWLEDGEMENTS.md](ACKNOWLEDGEMENTS.md) for acknowledgments.

---

## Support

- **Issues:** [GitHub Issues](https://github.com/AnubisXFramework/AnubisXFramework/issues)
- **Discussions:** [GitHub Discussions](https://github.com/AnubisXFramework/AnubisXFramework/discussions)
- **Security:** [SECURITY.md](SECURITY.md)

---

## License

This work is licensed under [Creative Commons Attribution 4.0 International](LICENSE.md) (CC BY 4.0).

---

**© 2026 Ahmed Awad (NullC0d3). All rights reserved.**  
*Original documentation, framework design, algorithms, source code, diagrams, and repository structure are the intellectual work of Ahmed Awad (NullC0d3), unless otherwise indicated. Third-party software, libraries, datasets, and referenced works remain the property of their respective owners and are governed by their own licenses.*

---

*Classification: PUBLIC (C0)*

