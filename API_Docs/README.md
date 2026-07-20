# API Documentation

**AnubisX Framework — API Reference**

---

## Official DOI

DOI: [10.5281/zenodo.21446923](https://doi.org/10.5281/zenodo.21446923)

This release is permanently archived on Zenodo under DOI: [https://doi.org/10.5281/zenodo.21446923](https://doi.org/10.5281/zenodo.21446923)

---

## Overview

The AnubisX Framework API provides programmatic access to the core attribution pipeline: feature extraction, profile construction, comparison, evidence fusion, and decision. The API is organized by domain.

## API Modules

| Module | Description | Endpoints |
|---|---|---|
| [Stylometry](Stylometry_API.md) | Linguistic feature extraction and comparison | `extract/stylometry`, `compare/stylometry` |
| [Chrono-Profiling](Chrono_API.md) | Temporal feature extraction and comparison | `extract/chrono`, `compare/chrono` |
| [Terminal Profiling](Terminal_API.md) | Interaction feature extraction and comparison | `extract/terminal`, `compare/terminal` |
| [Network Analysis](Network_API.md) | Social graph feature extraction and comparison | `extract/network`, `compare/network` |
| [Media Forensics](Media_API.md) | Environmental feature extraction and comparison | `extract/media`, `compare/media` |
| [Fusion](Fusion_API.md) | Multi-modal evidence fusion | `fusion/score`, `fusion/decision`, `fusion/feature` |
| [Attribution](Attribution_API.md) | LR computation and decision | `attribution/lr`, `attribution/decision` |

## Standard Response Format

All API responses follow a standardized format:

```json
{
  "status": "success" | "error",
  "data": { ... },
  "metadata": {
    "version": "1.0",
    "timestamp": "2026-01-01T00:00:00Z"
  }
}
```

## Authentication

API access requires authentication. See the [Getting Started Guide](../Getting_Started/) for details.

## Rate Limits

Standard API rate limits apply. Contact for higher limits under commercial license.

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


