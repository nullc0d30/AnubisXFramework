# Frequently Asked Questions

**AnubisX Framework**

---

## Official DOI

DOI: [10.5281/zenodo.21446923](https://doi.org/10.5281/zenodo.21446923)

This release is permanently archived on Zenodo under DOI: [https://doi.org/10.5281/zenodo.21446923](https://doi.org/10.5281/zenodo.21446923)

---

## General

### What is the AnubisX Framework?

The AnubisX Framework is a scientific methodology for digital identity attribution. Instead of relying on technical indicators like IP addresses or device fingerprints, it measures persistent human cognitive signatures — patterns of language, timing, interaction, and social behavior that are unique to each individual.

### What makes it different from existing attribution methods?

Traditional attribution tracks what adversaries *use* (IPs, devices, networks) — artifacts they can change at will. AnubisX tracks who adversaries *are* — involuntary cognitive patterns they cannot change. This makes attribution robust against technical countermeasures.

### What is Identity Intelligence (IdINT)?

Identity Intelligence is the proposed formal forensic discipline for behavioral identity attribution. The framework positions IdINT alongside established forensic disciplines like DNA analysis, fingerprinting, and ballistics.

### Is this framework implemented in software?

The AnubisX Framework is currently a complete theoretical specification: 31 axioms, 37+ algorithms, 292 mathematical definitions, 38 experiment designs, 24 benchmarks, 20 case studies, and a full validation framework. Software implementation is a planned next phase.

## Technical

### What are the five behavioral modalities?

1. **Forensic Stylometry** — Writing style and linguistic patterns
2. **Chrono-Profiling** — Temporal behavior and timing patterns
3. **Terminal Execution Profiling** — Human-machine interaction patterns
4. **Relational Network Analysis** — Social graph and communication patterns
5. **Environmental Media Forensics** — Digital environment and organizational habits

### How is attribution confidence quantified?

Attribution strength is expressed as a Likelihood Ratio (LR): the probability of observing the evidence if the samples come from the same source divided by the probability if they come from different sources. An LR of 100 means the evidence is 100 times more likely under the same-source hypothesis.

### What is the Cognitive Centroid?

The Cognitive Centroid is the theoretical fixed point in behavioral feature space toward which an individual's measured behavioral patterns converge. It represents the "center of gravity" of an individual's behavioral identity.

### What mathematical methods are used?

The framework uses Higher-Order Singular Value Decomposition (HOSVD) for feature-level fusion, Dempster-Shafer Theory for evidence combination, Likelihood Ratio calibration via pool-adjacent-violators (PAV) or logistic regression, and empirical cross-entropy for validation.

## Scientific Rigor

### Is the framework validated?

The framework includes 38 experiment designs, 24 benchmarks with 30 baselines, 20 case studies across 4 domains, and a four-tier validation hierarchy with quantified acceptance criteria. Empirical validation is the planned next phase following implementation.

### Is it peer reviewed?

The framework follows a formal publication pipeline with peer review, quality assurance, and publication flow governance. Planned publications will undergo standard scientific peer review.

### How does it meet Daubert standards?

The framework is designed for Daubert compliance: testable hypotheses (all axioms are empirically falsifiable), quantified error rates, peer-reviewed publication pipeline, formal protocols and standards, and foundations in established science.

## Ethics and Privacy

### What about privacy?

The framework embeds the Proportionality and Privacy Protection Protocol (P³) as a core architectural constraint. Attribution methods are proportional to investigative need; data collection follows the minimum necessary principle; and dual-use safeguards are documented.

### Could this be used for mass surveillance?

The framework is designed for forensic investigation contexts with legal oversight. The P³ Protocol explicitly constrains proportionality, and the framework's transparency requirements prevent covert deployment without detection.

## Usage

### Who should use this?

- **Forensic investigators** seeking rigorous attribution methodology
- **Cybersecurity analysts** tracking threat actors
- **Academic researchers** in behavioral forensics, stylometry, and identity science
- **Legal professionals** evaluating digital attribution evidence
- **Policy makers** developing standards for digital evidence

### How do I get started?

See the [Getting Started Guide](../Getting_Started/) for a step-by-step introduction.

### Can I use this commercially?

The framework is available under CC BY 4.0 for academic and research use. Commercial use requires a separate license. See the [LICENSE](../LICENSE.md).

## Development

### What is the current status?

The framework has completed all theoretical specifications: axioms, conceptual model, mathematics, algorithms, validation, benchmarks, experiments, case studies, publication roadmap, and IP strategy. The next phase is software implementation and empirical validation.

### How can I contribute?

See [CONTRIBUTING](../CONTRIBUTING.md) for contribution guidelines. We welcome contributions from researchers, practitioners, and collaborators aligned with the framework's scientific and ethical standards.

### Is the reference book available?

The document "You Can Hide Your Name... Not Your Mind" is included in the repository as a reference work on Identity Intelligence.

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


