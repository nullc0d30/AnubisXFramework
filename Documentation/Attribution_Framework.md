# Attribution Framework

**AnubisX Framework — LR-Based Attribution and Evidence Integration**

---

## Official DOI

DOI:
10.5281/zenodo.21393392

Persistent URL:
https://doi.org/10.5281/zenodo.21393392

This release is permanently archived on Zenodo under DOI: https://doi.org/10.5281/zenodo.21393392

---

## 1. Likelihood Ratio Framework

Attribution strength is quantified using the Likelihood Ratio:

```
LR = P(E | Hₚ) / P(E | H_d)
```

Where:
- E = observed behavioral evidence
- Hₚ = same-source hypothesis (the questioned and reference samples originate from the same individual)
- H_d = different-source hypothesis (the questioned and reference samples originate from different individuals)

### Interpretation

| LR Range | Evidence Strength |
|---|---|
| LR > 100 | Very strong support for same-source |
| 10 < LR ≤ 100 | Strong support for same-source |
| 3 < LR ≤ 10 | Moderate support for same-source |
| 1 < LR ≤ 3 | Limited support for same-source |
| LR = 1 | No support for either hypothesis |
| 0.33 < LR < 1 | Limited support for different-source |
| 0.1 < LR ≤ 0.33 | Moderate support for different-source |
| 0.01 < LR ≤ 0.1 | Strong support for different-source |
| LR ≤ 0.01 | Very strong support for different-source |

## 2. Evidence Weighting

Each piece of evidence is weighted along three dimensions before fusion:

- **Quality (Q)**: Intrinsic reliability of the evidence source
- **Relevance (R)**: Contextual applicability to the attribution question
- **Recency (T)**: Temporal degradation of evidence value

## 3. Multi-Modal Fusion

Fused LR combines weighted LRs from all five modalities using Dempster-Shafer Theory, producing a combined LR that accounts for inter-modality dependencies and conflicts.

## 4. Attribution Standards

- **Inconclusive outcomes**: Where LR is close to 1 or data is insufficient, the conclusion is marked inconclusive (DP-ATR-004)
- **Sensitivity analysis**: Conclusions are tested against reasonable variations in prior assumptions
- **Uncertainty bounds**: LR estimates include confidence intervals

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
