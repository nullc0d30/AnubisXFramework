# Multi-Modal Framework

**AnubisX Framework — Five Modalities and Fusion Architecture**

---

## Official DOI

DOI:
10.5281/zenodo.21393392

Persistent URL:
https://doi.org/10.5281/zenodo.21393392

This release is permanently archived on Zenodo under DOI: https://doi.org/10.5281/zenodo.21393392

---

## 1. The Five Modalities

### 1.1 Forensic Stylometry

Stylometric analysis measures involuntary linguistic patterns that are unique to each individual:

- Function-word frequency distributions
- Syntactic structure preferences
- Vocabulary richness and diversity
- Readability and complexity metrics
- Punctuation and formatting habits

### 1.2 Chrono-Profiling

Temporal behavior analysis captures patterns in how individuals interact with time:

- Circadian activity rhythms
- Inter-event timing distributions
- Response time patterns
- Temporal clustering and periodicity
- Time-of-day preferences for different activities

### 1.3 Terminal Execution Profiling

Human-machine interaction patterns reflect deeply ingrained procedural habits:

- Command sequence patterns
- Navigation path preferences
- Input timing and rhythm
- Error patterns and correction behavior
- Application and tool selection preferences

### 1.4 Relational Network Analysis

Social graph analysis captures individual-specific patterns in relationship structures:

- Network topology metrics
- Communication frequency and timing
- Group affiliation patterns
- Information propagation behavior
- Role and position within networks

### 1.5 Environmental Media Forensics

Digital environment analysis captures persistent organizational habits:

- File system structure and organization
- Naming convention patterns
- Metadata generation habits
- Tool and platform configuration preferences
- Workflow organization patterns

## 2. Fusion Architecture

### 2.1 Fusion Strategies

| Strategy | Description | Characteristics |
|---|---|---|
| Score-Level Fusion | Combine similarity scores before LR transformation | Simplest, most robust |
| Feature-Level Fusion | Concatenate feature vectors via HOSVD | Captures cross-modal interactions |
| Decision-Level Fusion | Combine independent modality decisions | Preserves independence |

### 2.2 Evidence Integration

1. Each modality produces a similarity score
2. Scores are calibrated to likelihood ratios
3. LRs are weighted by quality, relevance, and recency
4. Weighted LRs are fused using Dempster-Shafer Theory
5. Combined LR supports the final attribution decision

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
