# Security Policy

**AnubisX Framework — Responsible Disclosure and Security Guidelines**

**Source**: Research/Research_Limitations.md (RSR-003), Validation/Error_Analysis.md (VLD-006)

---

## Supported Versions

The AnubisX Framework v2.0.0 includes both a complete theoretical specification and a validated prototype implementation (Anubis Twitter v2.5). The prototype code is included in this repository. Security policies apply to both the specification and the prototype implementation.

| Version | Supported |
|---|---|
| 2.0.0 (specification + prototype) | Security review ongoing |
| < 2.0.0 | Not supported |

## Reporting a Vulnerability

The AnubisX Framework now includes prototype implementation code (Anubis Twitter v2.5). Security vulnerabilities should be reported responsibly.

### For Specification Issues

If you identify a security-relevant issue in the framework specification — such as a methodological weakness that could enable false attribution, a gap in error analysis, or a vulnerability in the evidence evaluation pipeline — please report it by:

1. **Opening a security issue** on GitHub with the `[SECURITY]` prefix in the title
2. **Contacting the maintainers** directly through the project's security contact
3. **Providing sufficient detail** to reproduce or understand the issue

### For Implementation Issues

Prototype code is now included in this repository. For implementation-specific vulnerabilities:

1. Do **not** publicly disclose the vulnerability
2. Report it to the project security team
3. Provide sufficient detail for reproduction and verification
4. Allow reasonable time for remediation before public disclosure

## Responsible Disclosure Guidelines

1. Report vulnerabilities promptly to the project maintainers
2. Do not publicly disclose until the issue has been addressed
3. Provide a clear description, potential impact, and any suggested remediation
4. Allow reasonable time for assessment and remediation based on severity
5. Act in good faith to avoid privacy violations, data destruction, or service disruption

## Scope

### In Scope

- Algorithm specifications that could produce systematic errors in attribution
- Error analysis gaps that could lead to incorrect conclusions
- Data handling procedures that could compromise privacy or security
- Implementation code (prototype available in repository)
- Validation framework completeness

### Out of Scope

- Theoretical limitations already documented in the framework (see Research/Research_Limitations.md)
- Design trade-offs explicitly acknowledged in specifications
- Known operating-environment dependencies documented in the framework

## Security Considerations

### Theoretical Limitations

The framework documents its own limitations in detail:

- [Research/Research_Limitations.md](Research/Research_Limitations.md) — all acknowledged limitations
- [Validation/Error_Analysis.md](Validation/Error_Analysis.md) — error decomposed into 5 components (measurement, sampling, algorithmic, model, operational)
- [Validation/False_Positive_Analysis.md](Validation/False_Positive_Analysis.md) — 6 false positive categories identified
- [Validation/False_Negative_Analysis.md](Validation/False_Negative_Analysis.md) — 6 false negative categories identified

### Data Privacy

The framework embeds privacy protections through the P³ Protocol (Proportionality and Privacy Protection), which is defined in the framework's governance documents:

- Data collection follows the minimum necessary principle
- Attribution methods are proportional to investigative need
- Access controls and audit trails provide accountability

### Adversarial Considerations

- HYP-CORE-004 (Involuntary Emission) provides the theoretical basis for counter-forensic resistance. **Source**: Axioms/Core_Axioms.md
- HYP-BEH-004 addresses the cost of deliberate behavioral modification. **Source**: Axioms/Behavior_Axioms.md
- Stress test experiments (EXP-ST-001—006) specifically test adversarial scenarios. **Source**: Experiments/Experiment_Catalog.md

## Prototype Security

The Anubis Twitter v2.5 prototype operates within the following security boundaries:

### Data Handling

- All prototype validation was conducted on **public Twitter data** from 31 Egyptian accounts
- Only publicly available tweets were collected via the Twitter API v2
- No direct messages, private account data, or non-public information was accessed
- Data was processed in compliance with Twitter's Terms of Service and applicable data protection regulations

### Prototype Code Security

- The prototype implements **stylometric feature extraction only** — no network scanning, system access, or privileged operations
- FAISS similarity search operates on **isolated feature vectors** with no external connections
- No credentials, API keys, or secrets are hard-coded in the prototype code
- The prototype does not perform any data exfiltration or external communication beyond the initial Twitter API data collection

### Known Limitations

- The prototype has not undergone formal security audit or penetration testing
- Single-modality implementation (stylometry only) limits the attack surface but also limits attribution robustness
- Production deployments require additional security hardening including encryption-at-rest, access controls, and audit logging

## Ethical Use

The AnubisX Framework is intended for legitimate forensic, security, and research purposes conducted under appropriate legal oversight. The project's ethical principles explicitly prohibit:

- Mass surveillance without legal authorization and proportionality
- Privacy violations beyond the minimum necessary for legitimate investigation
- Use for harassment, intimidation, or discrimination
- Deployment without transparency and accountability mechanisms

## Contact

Security reports should be directed to the project maintainers through GitHub security advisories or by opening a confidential issue.

---

**Project**: AnubisX Framework  
**Primary Author**: Ahmed Awad (NullC0d3)  
**Author Profile**: https://www.linkedin.com/in/nullc0d3/  
**ORCID**: https://orcid.org/0009-0005-0654-3393  
**Original Framework**: Ahmed Awad (NullC0d3)  
**Original Research**: Ahmed Awad (NullC0d3)  
**Repository**: [https://github.com/AnubisXFramework/AnubisXFramework](https://github.com/AnubisXFramework/AnubisXFramework)  

**Copyright** © 2026 Ahmed Awad (NullC0d3). All rights reserved.  
Original documentation, framework design, algorithms, source code, diagrams, and repository structure are the intellectual work of Ahmed Awad (NullC0d3), unless otherwise indicated. Third-party software, libraries, datasets, and referenced works remain the property of their respective owners and are governed by their own licenses.

**DOI**: [https://doi.org/10.5281/zenodo.21446923](https://doi.org/10.5281/zenodo.21446923)

---

*Classification: PUBLIC (C0)*


