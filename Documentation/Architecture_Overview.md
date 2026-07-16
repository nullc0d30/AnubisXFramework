# Architecture Overview

**AnubisX Framework — Component Architecture**

---

## Official DOI

DOI:
10.5281/zenodo.21393392

Persistent URL:
https://doi.org/10.5281/zenodo.21393392

This release is permanently archived on Zenodo under DOI: https://doi.org/10.5281/zenodo.21393392

---

## 1. Framework Architecture

The AnubisX Framework defines a five-stage pipeline for behavioral identity attribution:

```
Feature Extraction → Profile Construction → Profile Comparison → Evidence Integration → Decision
```

### 1.1 Stage 1: Feature Extraction

Each of the five behavioral modalities is processed by modality-specific extractors that transform raw behavioral data into structured feature vectors:

| Modality | Input Data | Feature Type |
|---|---|---|
| Stylometry | Text content | Function-word frequencies, syntax patterns |
| Chrono-Profiling | Timestamped activity | Temporal intervals, circadian patterns |
| Terminal Profiling | Interaction logs | Command sequences, timing patterns |
| Network Analysis | Social graph data | Graph topology, interaction metrics |
| Media Forensics | File system metadata | Organizational patterns, naming conventions |

### 1.2 Stage 2: Profile Construction

Extracted features are assembled into modality-specific profiles. Each profile is a structured representation of observed behavioral patterns for a given individual within a given modality.

### 1.3 Stage 3: Profile Comparison

Reference profiles (known individuals) are compared against questioned profiles (unknown subjects) using modality-specific similarity functions. Each comparison produces a similarity score.

### 1.4 Stage 4: Evidence Integration

Similarity scores are transformed into likelihood ratios (LRs) and fused across modalities. The framework supports three fusion strategies:

- **Score-level fusion**: Combining similarity scores before LR transformation
- **Decision-level fusion**: Combining independent modality decisions
- **Feature-level fusion**: Concatenating feature vectors (via HOSVD)

### 1.5 Stage 5: Decision

The fused evidence supports a decision under quantified uncertainty. Outputs include:

- Likelihood Ratio quantifying evidence strength
- Attribution Confidence Metric
- Inconclusive determination where evidence is insufficient

## 2. Information Flow

```
Raw Data → [Feature Extractors] → Feature Vectors → [Profile Constructor] → Behavioral Profiles → [Comparator] → Similarity Scores → [Calibrator] → LRs → [Fusion Engine] → Combined LR → [Decision Module] → Attribution Conclusion
```

## 3. Constraints

- **Observational Bound**: Attribution confidence is fundamentally limited by the quantity and quality of available observations (HYP-CORE-004)
- **Proportionality**: Evidence collection must be proportional to investigative need (P³ Protocol)
- **Uncertainty Quantification**: All conclusions must include quantified uncertainty

---

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
