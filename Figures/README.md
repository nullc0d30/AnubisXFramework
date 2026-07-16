# Figures — AnubisX Framework

**Publication-Ready Figure Specifications**

**Date:** July 16, 2026  
**Classification:** PUBLIC (C0)

---

This directory contains specifications for all figures required by the AnubisX Framework foundational paper. Figures should be generated using the experimental data from the prototype implementation and the specified design requirements.

---

## Figure Specifications

### Figure 1: Authorship Attribution Research Timeline

**Caption:** Timeline of key developments in authorship attribution and behavioral identity research, contextualizing the AnubisX Framework within the broader research landscape.

**Purpose:** To situate the framework within the historical development of computational stylometry, digital forensics, and behavioral biometrics.

**Manuscript Section:** Section 3 (Related Work)

**Content:**
- Milestones from Mosteller & Wallace (1964) to present
- Key events: PAN workshop series (2010–2025), Sentence-BERT (2019), Arabic NLP developments
- AnubisX Framework placement at v1.0 (2026) and v2.0 (2026)

**Design Requirements:**
- Horizontal timeline layout
- 10–15 milestone markers with labels
- Distinguishable phases: Classical, Computational, Deep Learning, Integrative
- Color-coded by research domain

---

### Figure 2: AnubisX Framework Architecture

**Caption:** The six-layer architecture of the AnubisX Framework showing the data flow from ingestion through feature extraction, profile construction, comparison, evidence evaluation, and decision, with the three supported workflows.

**Purpose:** To provide a visual overview of the complete framework architecture.

**Manuscript Section:** Section 8 (System Architecture)

**Content:**
- Six layers: Data, Feature, Profile, Comparison, Evidence, Decision
- Data flow arrows between layers
- Three workflow indicators: Identification (1:N), Verification (1:1), Forensic Comparison (1:1 with LR)
- Five modality icons (stylometry, chrono, terminal, network, media)

**Design Requirements:**
- Layered block diagram
- Vertical flow from bottom to top
- Clear labeling for each layer
- Workflow indicators on the side
- Publication-ready at 300 DPI

---

### Figure 3: Stylometric Fingerprint Extraction Pipeline

**Caption:** The stylometric fingerprint extraction pipeline showing the construction of 372-dimensional feature vectors from raw Twitter data, combining transformer embeddings, lexical features, and character n-gram features.

**Purpose:** To illustrate the fingerprint construction process implemented in the Anubis Twitter v2.5 prototype.

**Manuscript Section:** Section 9 (Prototype Implementation) and Section 11 (Experimental Results)

**Content:**
- Raw tweet data → preprocessing → feature extraction
- Three parallel branches: embedding (256-dim), lexical stats (16-dim), character n-grams (100-dim)
- Concatenation to 372-dim fingerprint vector
- FAISS index construction

**Design Requirements:**
- Pipeline flowchart
- Three parallel extraction branches
- Dimension annotations at each stage
- Color-coding for data type (text, numeric, vector)

---

### Figure 4: Cross-User Cosine Similarity Distribution

**Caption:** Distribution of cosine similarity scores across 465 cross-user identity pairs from 31 Egyptian Twitter accounts, showing mean 0.697 (σ = 0.105) with 256-dim embedding dominance.

**Purpose:** To visualize the cross-user similarity results from EXP-002 and demonstrate the embedding dominance effect.

**Manuscript Section:** Section 11 (Experimental Results, Table 7)

**Content:**
- Histogram of 465 cosine similarity values
- Normal curve overlay
- Annotated mean (0.697) and standard deviation (0.105)
- Threshold lines at 0.5, 0.7, 0.9
- Percentage annotations for each region

**Design Requirements:**
- Histogram with kernel density estimate
- Clean, academic-style visualization
- Clear axis labels with font size >= 10pt
- Color-blind friendly palette

---

### Figure 5: Operational Deployment Scenarios

**Caption:** Four operational deployment scenarios for the AnubisX Framework: (a) SOC integration for anonymous actor linking, (b) digital forensic investigation workflow, (c) cross-platform OSINT identity resolution, (d) coordinated inauthentic behavior detection.

**Purpose:** To illustrate the practical applications discussed in Section 13 (Practical Implications).

**Manuscript Section:** Section 13 (Practical Implications)

**Content:**
- Four sub-panels (a–d)
- Scenario a: SOC analyst workflow with AnubisX as complementary signal
- Scenario b: LR-based evidence grading in forensic context
- Scenario c: Cross-platform identity resolution pipeline
- Scenario d: Network-level coordination detection

**Design Requirements:**
- Four-panel layout (2x2 grid)
- Simplified workflow diagrams for each scenario
- Consistent iconography across panels
- Professional, publication-quality appearance

---

### Figure 6: Research and Development Roadmap

**Caption:** The AnubisX Framework research and development roadmap spanning five years, showing the progression from theoretical foundation through prototype validation to operational deployment.

**Purpose:** To visualize the development timeline from the ROADMAP_v2.md document.

**Manuscript Section:** Section 15 (Future Work)

**Content:**
- Five-year timeline (2026–2030)
- Phases: Implementation, Validation, Publications, Community, Advanced Research
- Milestone markers with completion status
- Dependency arrows between phases

**Design Requirements:**
- Gantt chart or phase diagram
- Five horizontal swimlanes for phases
- Completed items in green, in-progress in yellow, planned in blue
- Clear date markers on x-axis

---

### Figure 7: Evidence Evaluation Workflow

**Caption:** The evidence evaluation workflow showing score calibration to likelihood ratios, multi-modal fusion, and decision threshold comparison.

**Purpose:** To illustrate the evidence processing pipeline from the Comparison Layer through the Decision Layer.

**Manuscript Section:** Section 8 (System Architecture) and Section 7 (Mathematical Framework)

**Content:**
- Score vector input from similarity comparison
- Calibration step (PAV/logistic regression → LR)
- Multi-modal fusion (score-level, feature-level, decision-level)
- Threshold comparison block
- Three outputs: Attribution, Exclusion, Inconclusive

**Design Requirements:**
- Process flow diagram
- Decision diamond for threshold comparison
- Parallel fusion branches
- Output indicators with LR ranges

---

## Generation Notes

All figures should be generated using the actual experimental data from the Anubis Twitter v2.5 prototype where applicable (Figures 3, 4). Figures 1, 2, 5, 6, and 7 may use designed layouts based on the framework specification.

**Recommended Tools:**
- Matplotlib + Seaborn (Python) for Figures 4
- Draw.io / diagrams.net for Figures 1, 2, 3, 5, 6, 7
- Adobe Illustrator for final publication-ready versions

## File Naming Convention

```
Figure_01_Research_Timeline.png
Figure_02_Framework_Architecture.png
Figure_03_Fingerprint_Pipeline.png
Figure_04_Similarity_Distribution.png
Figure_05_Deployment_Scenarios.png
Figure_06_Research_Roadmap.png
Figure_07_Evidence_Workflow.png
```

## Resolution Requirements

- Print publication: 300 DPI minimum
- Online publication: 150 DPI minimum
- Dimensions: Width 3.5 in (single column) to 7 in (double column)

---

**Project**: AnubisX Framework  
**Primary Author**: Ahmed Awad (NullC0d3)  
**Repository**: [https://github.com/nullc0d30/AnubisXFramework](https://github.com/nullc0d30/AnubisXFramework)  
**DOI**: [https://doi.org/10.5281/zenodo.21393392](https://doi.org/10.5281/zenodo.21393392)

**Copyright** © 2026 Ahmed Awad (NullC0d3). All rights reserved.

*Classification: PUBLIC (C0)*
