# Attribution API

**AnubisX Framework — LR Computation and Decision Endpoints**

---

## Official DOI

DOI:
10.5281/zenodo.21393392

Persistent URL:
https://doi.org/10.5281/zenodo.21393392

This release is permanently archived on Zenodo under DOI: https://doi.org/10.5281/zenodo.21393392

---

## `POST /attribution/lr`

Computes the Likelihood Ratio for a questioned sample against a reference profile.

### Request Body

```json
{
  "reference_profile_id": "profile-xxx",
  "questioned_sample": { ... },
  "modalities": ["stylometry", "chrono", "terminal", "network", "media"],
  "options": {
    "calibration": "pav" | "logistic",
    "prior": { "same_source": 0.5 }
  }
}
```

### Response

```json
{
  "status": "success",
  "data": {
    "lr": 150.0,
    "log_lr": 2.176,
    "modality_contributions": {
      "stylometry": { "lr": 45.0, "weight": 0.3 },
      "chrono": { "lr": 12.0, "weight": 0.2 },
      "terminal": { "lr": 8.0, "weight": 0.2 },
      "network": { "lr": 3.0, "weight": 0.15 },
      "media": { "lr": 2.0, "weight": 0.15 }
    },
    "ece": 0.12,
    "confidence_interval": [120.0, 187.5]
  }
}
```

## `POST /attribution/decision`

Produces a binary or categorical decision based on the LR.

### Request Body

```json
{
  "lr": 150.0,
  "threshold_same_source": 100.0,
  "threshold_different_source": 0.01
}
```

### Response

```json
{
  "status": "success",
  "data": {
    "decision": "same_source",
    "strength": "very_strong",
    "lr": 150.0
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
