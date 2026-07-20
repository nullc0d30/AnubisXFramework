# Benchmarking Guide

**AnubisX Framework — Benchmark Specifications and Evaluation Scenarios**

---

## Official DOI

DOI: [10.5281/zenodo.21446923](https://doi.org/10.5281/zenodo.21446923)

This release is permanently archived on Zenodo under DOI: [https://doi.org/10.5281/zenodo.21446923](https://doi.org/10.5281/zenodo.21446923)

---

## 1. Benchmark Framework

The benchmark library provides standardized evaluation protocols for behavioral attribution systems.

### 1.1 Benchmark Categories

| Category | Focus | Example Benchmarks |
|---|---|---|
| Within-Platform | Attribution within a single platform | Twitter stylometry, Facebook chrono-profiling |
| Cross-Platform | Attribution across different platforms | Twitter ↔ Facebook identity resolution |
| Counter-Forensic | Attribution under obfuscation | Style-shifting resistance, LLM obfuscation |
| Robustness | Performance under data degradation | Missing modalities, noise injection |

### 1.2 Baseline Methods

Results are compared against established baseline methods to demonstrate improvement:

- **Random baseline**: Chance-level performance
- **Single-modality baseline**: Performance of each modality individually
- **Existing methods**: Published state-of-the-art methods where applicable

## 2. Evaluation Scenarios

| Scenario | Description | Key Requirement |
|---|---|---|
| Closed-Set Identification | Identify a subject from a known set | Top-1 accuracy |
| Open-Set Identification | Determine if subject is in a known set | Rejection capability |
| Verification | Verify claimed identity | FPR/FNR trade-off |
| Forensic Comparison | Source attribution of questioned material | LR quantification |

## 3. Reporting Standards

All benchmark results must report:

- Dataset characteristics and limitations
- Experimental protocol (train/test split, cross-validation)
- Metric values with confidence intervals
- Statistical significance testing
- Comparison with baselines

---

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


