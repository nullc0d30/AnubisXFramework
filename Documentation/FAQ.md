# Frequently Asked Questions

**AnubisX Framework v2.0**

---

## Official DOI

DOI:
10.5281/zenodo.21393392

Persistent URL:
https://doi.org/10.5281/zenodo.21393392

This release is permanently archived on Zenodo under DOI: https://doi.org/10.5281/zenodo.21393392

---

## General Questions

### What is the AnubisX Framework?

A scientific methodology for digital identity attribution based on invariant human cognitive signatures. It provides a formal theoretical foundation, mathematical framework, algorithms, validation methodology, and prototype implementation for behavioral identity attribution.

### How is it different from traditional attribution?

Traditional attribution tracks what adversaries use (IPs, devices, accounts). AnubisX tracks who adversaries are — involuntary cognitive patterns (language habits, timing patterns, interaction styles) that they cannot easily change. Technical artifacts can be spoofed; cognitive patterns cannot.

### What are the five modalities?

1. **Forensic Stylometry**: Linguistic patterns (function-word frequencies, syntax preferences)
2. **Chrono-Profiling**: Temporal behavior patterns (circadian rhythms, inter-event timing)
3. **Terminal Execution Profiling**: Human-machine interaction patterns (command sequences, timing)
4. **Relational Network Analysis**: Social graph patterns (network topology, communication)
5. **Environmental Media Forensics**: Digital organization patterns (file structures, naming conventions)

### Is it implemented?

The framework has a validated prototype — Anubis Twitter Intelligence v2.5. This prototype implements the stylometric modality for the Twitter/X platform, with 31 Egyptian Twitter accounts fingerprinted at 372 dimensions and FAISS search verified at 16 microseconds.

### What is Identity Intelligence (IdINT)?

A proposed formal forensic discipline for behavioral identity attribution, alongside DNA analysis, fingerprinting, and ballistics. IdINT argues that cognitive traces are equally individual-specific as physical traces and should be recognized as a distinct class of forensic evidence.

### Is it peer reviewed?

The framework follows a formal publication pipeline with 6 planned papers covering framework, theory, mathematics, algorithms, validation, and case studies. Current validation is internal but follows rigorous scientific standards with 33 acceptance criteria and 23 metrics.

### How is confidence quantified?

Attribution strength is expressed as a Likelihood Ratio — the probability of the observed evidence under the same-source hypothesis divided by the probability under the different-source hypothesis. LR values range from <0.01 (very strong support for different-source) to >100 (very strong support for same-source).

### What about privacy?

The Proportionality and Privacy Protection Protocol (P3) is embedded in the core architecture, ensuring ethical constraints on attribution methods. Evidence collection must be proportional to investigative need.

### Who should use this?

Forensic investigators, cybersecurity analysts, academic researchers, legal professionals, and policy makers interested in behavioral identity attribution.

---

## Framework Questions

### How is the framework structured?

Six layers: Data Layer (acquisition) → Feature Layer (extraction) → Profile Layer (construction) → Comparison Layer (matching) → Evidence Layer (fusion) → Decision Layer (output). Six processing stages: Extract → Construct → Compare → Calibrate → Fuse → Decide.

### What are the three primary workflows?

1. **Identification**: Who is this? (1:N matching against database)
2. **Verification**: Is this who they claim to be? (1:1 matching)
3. **Forensic Comparison**: Source attribution of questioned material (LR quantification)

### How does multi-modal fusion work?

Three fusion strategies:
- **Score-level**: Combine similarity scores before LR transformation (simplest, most robust)
- **Feature-level**: Concatenate feature vectors via HOSVD (captures cross-modal interactions)
- **Decision-level**: Combine independent modality decisions (preserves independence)

### What validation does the framework have?

A four-tier hierarchy (Unit, Component, System, Operational) with 33 acceptance criteria, 13 accuracy metrics, 10 performance metrics, 24 benchmarks, and 30 baselines. 15 experiments have been executed on the prototype.

---

## Prototype Questions

### What does the prototype do?

The Anubis Twitter Intelligence v2.5 prototype implements stylometric fingerprinting for Twitter/X accounts. It can extract 372-dimensional behavioral fingerprints from tweet text, search for similar accounts using FAISS, verify Egyptian demographic affiliation, and visualize data through a Django dashboard.

### How many accounts have been fingerprinted?

31 Egyptian Twitter accounts have been fingerprinted, producing 372-dimensional stylometric feature vectors.

### How fast is the similarity search?

FAISS IndexFlatIP search runs at approximately 16 microseconds per query against the indexed database.

### What is the mean cross-user similarity?

The mean cosine similarity between different users is approximately 0.26, indicating good discriminability.

### What are the prototype limitations?

- **MarBERT/AraBERT unavailable**: HuggingFace authentication errors prevent loading these models; ensemble may silently degrade to single MPNet model
- **No timestamps**: Twitter scraper sets all timestamps to datetime.now(), making temporal features invalid
- **No interactions**: No reply, retweet, or like data collected
- **FAISS dimension mismatch**: 734-dim legacy scripts incompatible with 372-dim pipeline
- **Only stylometry implemented**: 4 of 5 modalities not operational
- **Facebook/cross-platform**: Not implemented

---

## Validation Questions

### What experiments have been executed?

15 experiments covering:
- Stylometric fingerprint extraction from 31 users
- Ensemble embedding validation (3-model weighted ensemble)
- Lexical feature extraction (TTR, word length, punctuation, emoji)
- TF-IDF topic vector extraction
- FAISS index construction and similarity search
- Cross-user similarity distribution analysis
- Egyptian account verification (3-layer scoring)
- Publication readiness assessment
- Prototype capability catalog

### What metrics are available?

7 of 13 accuracy metrics are computable from current data: similarity distributions, feature statistics, search latency. Formal accuracy metrics (FAR, FRR, AUC, EER, Cllr, d-prime) require ground-truth verification data not yet available.

### Is the framework scientifically validated?

Partially. The theoretical framework (axioms, assumptions, algorithms, mathematics) is fully specified and internally consistent. The prototype demonstrates functional capability for stylometric fingerprinting. However, formal validation against acceptance criteria (33 total) requires additional data collection (timestamps, interactions, cross-platform) and ground-truth verification.

---

## Reproducibility and Data Questions

### Can I reproduce the results?

The prototype code and documentation are available. Reproducibility requires:
- Python 3.11 with sentence-transformers, torch, numpy, pandas, sklearn, faiss
- HuggingFace access for model downloads (~2GB)
- Twitter/X data (can be collected via scraping or API)
- Manual login for Twitter scraping
- Note: MarBERT/AraBERT auth errors may prevent exact reproduction

### What dataset is used?

31 Egyptian Twitter accounts were analyzed. The dataset limitations include: no ground-truth identity labels, no timestamps, no interaction data, small sample size (single demographic, single platform).

### What are the main research gaps?

1. **Empirical validation**: 33 acceptance criteria untested against real data
2. **Cross-platform validation**: Facebook and cross-platform pipelines not operational
3. **Multi-modal validation**: Only stylometry implemented
4. **Accuracy measurement**: No formal FAR/FRR/AUC estimates
5. **Dataset limitations**: Small, single-demographic, single-platform

---

## Contributing and Citing

### How can I contribute?

See the governance documentation for contribution guidelines, peer review process, and quality assurance standards. Contributions in the following areas are especially welcome: cross-platform implementation, temporal feature extraction, interaction data collection, formal validation studies, and additional demographic testing.

### How do I cite AnubisX?

Citation format will be established with the first publication release. For now, reference the framework by name and version (AnubisX Framework v2.0), with a link to the repository.

### What is the license?

CC BY 4.0 (Creative Commons Attribution 4.0 International).

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
*Version: 1.0*
