# Fusion API

**AnubisX Framework — Multi-Modal Evidence Fusion Endpoints**

---

## Official DOI

DOI:
10.5281/zenodo.21393392

Persistent URL:
https://doi.org/10.5281/zenodo.21393392

This release is permanently archived on Zenodo under DOI: https://doi.org/10.5281/zenodo.21393392

---

## `POST /fusion/score`

Fuses modality-level similarity scores using score-level fusion.

## `POST /fusion/decision`

Fuses independent modality decisions using decision-level fusion.

## `POST /fusion/feature`

Fuses modality feature vectors using HOSVD-based feature-level fusion.

## Common Response Format

```json
{
  "status": "success",
  "data": {
    "combined_lr": 150.0,
    "method": "dempster_shafer",
    "modalities_fused": 5,
    "conflict_coefficient": 0.05,
    "fusion_gain": 2.5
  }
}
```

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
