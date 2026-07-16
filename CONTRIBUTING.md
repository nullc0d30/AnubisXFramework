# Contributing to the AnubisX Framework

Thank you for your interest in contributing. This project follows rigorous scientific and ethical standards. All contributions must be consistent with the framework's axiomatic foundation and classification policies.

**Source**: CODE_OF_CONDUCT.md, CONFIDENTIALITY_POLICY.md

---

## Table of Contents

- [Code of Conduct](#code-of-conduct)
- [Types of Contributions](#types-of-contributions)
- [Getting Started](#getting-started)
- [Contribution Workflow](#contribution-workflow)
- [Standards and Guidelines](#standards-and-guidelines)
- [Ethical Guidelines](#ethical-guidelines)
- [Review Process](#review-process)
- [Questions](#questions)

---

## Code of Conduct

All contributors must abide by the [Code of Conduct](CODE_OF_CONDUCT.md). Harassment, discrimination, and unethical behavior will not be tolerated.

---

## Types of Contributions

### Reporting Issues

- **Bug reports**: Open an issue with a clear description, steps to reproduce, and expected versus actual behavior
- **Feature requests**: Describe the proposed addition, its rationale, and alignment with the framework's axiomatic foundation
- **Documentation improvements**: Suggestions for clarification, corrections, or additions to any document
- **Research questions**: Proposals for extending or challenging the theoretical framework

### Pull Requests

- **Algorithm implementations**: Implementations of the 37+ specified algorithms in any programming language
- **Mathematical refinements**: Corrections or extensions to the mathematical framework, consistent with the 31 axioms
- **Validation contributions**: New validation protocols, metrics, or baseline methods
- **Experimental validation**: The framework specifies 38 experiments — 15 have been executed via the Anubis Twitter v2.5 prototype. Contributions for the remaining **23 experiments** are especially welcome (see [Experiments/Experiment_Index.md](Experiments/Experiment_Index.md))
- **Multi-modality integration**: Extend the prototype beyond stylometry into chrono-profiling, terminal execution profiling, relational network analysis, or environmental media forensics
- **Documentation**: Clarifications, translations, or supplementary materials
- **Case studies**: Additional scenarios demonstrating framework application
- **Benchmark contributions**: New benchmark datasets or baseline methods

---

## Getting Started

1. **Read the framework documentation**: Start with [Documentation/Overview.md](Documentation/Overview.md) and [Documentation/Getting_Started.md](Documentation/Getting_Started.md)
2. **Review the prototype implementation**: See [Anubis Twitter/](Anubis%20Twitter/) for the validated prototype code — this serves as the reference implementation for stylometric fingerprinting and FAISS-based comparison
3. **Understand the axiomatic foundation**: Review [Axioms/Core_Axioms.md](Axioms/Core_Axioms.md) — contributions must be consistent with the 31 axioms across 6 groups (CORE, BEH, IDN, ATR, EVI, RSN)
4. **Review this document thoroughly**
5. **Fork the repository**: Create your own copy to work in
6. **Create a branch**: Use a descriptive name (`feature/your-feature`, `fix/issue-description`, `docs/topic`)

---

## Contribution Workflow

### Step 1: Open an Issue

Before starting work, open an issue describing what you plan to do. This prevents duplicate effort and allows maintainers to provide guidance.

### Step 2: Fork and Branch

```
git checkout -b feature/your-feature
```

### Step 3: Make Changes

Follow the framework's documentation and specification standards:

- **Mathematical contributions**: Use the framework's standardized mathematical notation as defined in the Mathematics/ directory
- **Algorithm contributions**: Reference the relevant ALG- identifier (ALG-001—036, 041) from the algorithm catalog
- **Documentation**: Use precise, measured language appropriate for a scientific audience. Avoid promotional claims. Quantify claims whenever possible
- **New content**: Must be consistent with the 31 axioms and the framework's classification system (C0—C4). Only C0 content may be submitted for public contributions

### Step 4: Self-Review

Before submitting, verify:

- [ ] Content is consistent with the framework's axioms
- [ ] All claims are quantified or identified as hypotheses
- [ ] Limitations and uncertainties are acknowledged
- [ ] Classification level is appropriate (C0 for public contributions)
- [ ] Cross-references use framework identifiers (AXIOM-, ALG-, EQ-, etc.)
- [ ] No confidential or proprietary information is included
- [ ] No internal paths or references from source materials are present

### Step 5: Submit a Pull Request

Submit a pull request with a clear title, a description of changes, references to related issues, and any dependencies on other pending changes.

---

## Standards and Guidelines

### Scientific Standards

- All contributions must be consistent with the framework's 31 formal axioms
- Empirical claims must be accompanied by evidence or explicitly marked as hypotheses
- Mathematical formulations must use the framework's standardized notation
- Limitations and uncertainties must be acknowledged
- No fabricated citations: all references must trace to approved repository documents or external published sources with full bibliographic details

### Documentation Standards

- Use clear, precise language appropriate for a scientific audience
- Avoid promotional or marketing language
- Include classification level (C0 for public contributions)
- Use proper cross-references to framework identifiers
- Follow the document structure used in Documentation/

### Code Standards

- Implementations should reference the relevant ALG- specification
- Include unit tests demonstrating correctness against the framework's acceptance criteria (AC-001—004)
- Document dependencies and build requirements
- Follow language-specific best practices

---

## Ethical Guidelines

### Privacy and Proportionality

- Do not submit personal data or personally identifiable information
- Attribution methods must respect the P³ Protocol (Proportionality and Privacy Protection) as defined in the framework's ethical guidelines
- Data collection must follow the minimum necessary principle

### Responsible Disclosure

- Acknowledge dual-use implications of any contribution
- Document potential for misuse and appropriate safeguards
- Do not submit methods designed for mass surveillance or privacy violations

### Scientific Integrity

- All contributions must acknowledge limitations and uncertainties
- Avoid overstatement of results or capabilities
- Clearly distinguish between established knowledge, hypotheses, and speculation

---

## Review Process

All contributions are subject to review:

1. **Initial review**: A maintainer reviews the contribution for scope and standards compliance
2. **Technical review**: Domain-specific reviewers evaluate mathematical or algorithmic correctness
3. **Ethical review**: Contributions are assessed against the framework's ethical guidelines and the P³ Protocol
4. **Integration**: Approved contributions are merged and cross-referenced

Review timelines depend on complexity. Simple documentation fixes are typically reviewed within 1—2 weeks. Substantive scientific contributions may require 4—8 weeks.

---

## Questions

- Check the [FAQ](Documentation/FAQ.md)
- Open a discussion on GitHub
- Review existing issues for similar questions

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
