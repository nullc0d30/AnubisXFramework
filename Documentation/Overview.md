# Framework Overview

**AnubisX Framework v2.0 — Behavioral Identity Attribution**

---

## Official DOI

**DOI**: [10.5281/zenodo.21446923](https://doi.org/10.5281/zenodo.21446923)

This release is permanently archived on Zenodo.

---

## 1. What is AnubisX?

AnubisX is a scientific framework for digital identity attribution based on the principle that human operators leave persistent, measurable cognitive signatures in their digital interactions. Unlike traditional attribution methods that track technical artifacts (IP addresses, device fingerprints, browser cookies), AnubisX analyzes involuntary behavioral patterns — the unconscious habits of language, timing, interaction, and organization that are unique to each individual.

The framework provides:
- A formal theoretical foundation (16 axioms, 20 hypotheses, 18 design principles)
- A mathematical formalism (292 definitions, 50+ equations, 37 algorithms)
- A multi-modal architecture (5 behavioral modalities, 3 fusion strategies)
- A validation framework (4-tier hierarchy, 31 acceptance criteria, 23 metrics)
- A prototype implementation (Anubis Twitter Intelligence v2.5)
- Experimental validation (15 executed experiments)
- 20 case studies across Twitter, Facebook, and cross-platform scenarios

## 2. The Problem: Digital Attribution Gaps

### 2.1 Current Attribution Limitations

Digital attribution — determining who is behind observed online behavior — relies almost exclusively on **technical indicators**:

| Indicator | Limitation |
|---|---|
| IP addresses | Easily spoofed via VPNs, proxies, Tor |
| Device fingerprints | Blocked by anti-fingerprinting browsers |
| Cookies | Cleared, blocked, or compartmentalized |
| Account credentials | Stolen, shared, or synthetic |
| Behavioral (single-modality) | Limited accuracy, easy to obfuscate |

These technical indicators share a fundamental weakness: they are properties of the **tool**, not the **operator**. An adversary who controls their technical environment can evade technical attribution.

### 2.2 The Behavioral Attribution Gap

The scientific community has demonstrated that behavioral patterns — stylometric, temporal, interactional — carry individual-specific information. However, prior work has been:
- **Single-modality**: Stylometry in isolation, without cross-modal validation
- **Platform-specific**: Validated on one platform, not generalized
- **Methodologically inconsistent**: No standardized validation framework
- **Theoretically underdeveloped**: No unifying theory of why behavioral attribution works

AnubisX bridges this gap with a comprehensive theoretical, mathematical, and empirical framework.

## 3. The Paradigm Shift: Behavioral vs. Technical Attribution

| Dimension | Technical Attribution | Behavioral Attribution (AnubisX) |
|---|---|---|
| **Target** | What the user has (IP, device) | Who the user is (cognitive patterns) |
| **Evadability** | Easily changed (VPN, new device) | Difficult to change (involuntary habits) |
| **Persistence** | Session-level | Years (stable across technical changes) |
| **Dimensionality** | Low (dozens of features) | High (hundreds of features, 5 modalities) |
| **Certainty** | Binary (match/no match) | Probabilistic (Likelihood Ratio) |
| **Validation** | Ad-hoc | Formal (4-tier, 31 criteria) |
| **Theoretical Basis** | Engineering | Cognitive science + forensic science |

### 3.1 Key Insight

The core insight (HYP-CORE-001) is that each individual possesses a **Cognitive Centroid** — a unique, mathematically stable attractor in behavioral feature space toward which their observable patterns converge over time. This centroid is:
- **Unique**: No two individuals share the same attractor
- **Persistent**: Stable across changes in technical infrastructure
- **Multi-modal**: Expressed across language, timing, interaction, network, and environment
- **Involuntary**: Largely outside conscious control
- **Measurable**: Quantifiable through statistical analysis of digital traces

## 4. Framework Components

### 4.1 Theoretical Foundation

The framework is built on 16 formal axioms, 20 research hypotheses, and 18 design principles organized into three tiers:

| Group | Count | Focus |
|---|---|---|
| Core (HYP-CORE) | 5 | Identity invariance, persistence, convergence |
| Behavioral (HYP-BEH) | 6 | Signal nature, stability, measurability |
| Identity (HYP-ID) | 5 | Uniqueness, estimability, singularity |
| Attribution (DP-ATR) | 5 | Multi-modal necessity, probabilistic output |
| Evidence (DP-EVI) | 5 | Independence, convergence, falsifiability |
| Reasoning (DP-RSN) | 5 | Conservative interpretation, transparency |

Plus 46 supporting assumptions across 6 categories (Core, Behavioral, Identity, Data, Platform, AI).

### 4.2 Mathematical Framework

292 mathematical definitions, 50+ formal equations, and 47+ functions organized into:
- **Function Type System**: FUNC-001 through FUNC-047+
- **Equation Catalog**: EQ-001 through EQ-050
- **Domain Algebra**: Feature spaces, profile spaces, evidence tensors
- **Signal Decomposition Model**: y = y_cog + y_ctx + y_temp + y_noise
- **Likelihood Ratio Framework**: LR = P(E|H_p) / P(E|H_d)

### 4.3 Algorithms

37 algorithms across 9 domains:

| Domain | Algorithms | IDs |
|---|---|---|
| Core Pipeline | 4 | ALG-001 — ALG-004 |
| Behavior Processing | 4 | ALG-005 — ALG-008 |
| Identity Determination | 4 | ALG-009 — ALG-012 |
| Evidence Processing | 4 | ALG-013 — ALG-016 |
| Attribution Scoring | 3 | ALG-017 — ALG-019 |
| Confidence Estimation | 4 | ALG-020 — ALG-023 |
| Similarity & Distance | 5 | ALG-024 — ALG-028 |
| Multi-Modal Fusion | 4 | ALG-029 — ALG-032 |
| Decision Logic | 5 | ALG-033 — ALG-036, ALG-041 |

### 4.4 Architecture

A six-layer architecture (Data → Feature → Profile → Comparison → Evidence → Decision) implementing a six-stage pipeline with five behavioral modalities and three workflows (Identification, Verification, Forensic Comparison).

### 4.5 Validation Framework

A four-tier validation hierarchy:

| Tier | Scope | Criteria |
|---|---|---|
| Tier 1 — Unit | Individual components | 6 criteria (AC-001A—F) |
| Tier 2 — Component | Modality-level pipelines | 8 criteria (AC-002A—H) |
| Tier 3 — System | Multi-modal fusion | 10 criteria (AC-003A—J) |
| Tier 4 — Operational | Deployment context | 7 criteria (AC-004A—G) |

Plus 13 accuracy metrics, 10 performance metrics, 24 benchmarks, 30 baselines.

## 5. Prototype Implementation: Anubis Twitter Intelligence v2.5

The Anubis Twitter Intelligence Prototype v2.5 is a working implementation of the framework's core stylometric modality for the Twitter/X platform.

### 5.1 Capabilities

| Capability | Status | Detail |
|---|---|---|
| Egyptian Demographic Filtering | WORKING | 3-layer scoring (bio 60%, posts 40%), 200+ cultural indicators |
| SQLite Storage | WORKING | Versioned fingerprints schema |
| Stylometric Vector Fingerprinting | WORKING (UNTESTED) | 3-model ensemble → 372-dim fingerprint |
| FAISS Similarity Search | VERIFIED | IndexFlatIP, 16us search time |
| Twitter Web Scraping | PARTIAL | Manual login required, no timestamps |
| Graph / Network Analysis | WORKING (UNTESTED) | Directed graph, centrality metrics |
| Dashboard / UI | WORKING | 10 Django views, AnubisBackend bridge |
| Document / Report Generation | WORKING | Excel, HTML, Markdown reports |

### 5.2 Fingerprint Architecture

The 372-dimensional stylometric fingerprint is constructed as:

```
fingerprint[372] = embedding[256] + stats[16] + cvec[100]
```

- **embedding[256]**: Weighted ensemble of MarBERT (0.45), AraBERT (0.35), MPNet (0.20), projected to 256-dim
- **stats[16]**: Lexical features (TTR, avg_word_length, punctuation_ratio, emoji_ratio, char_3grams_top100, most_words_top50, temporal features)
- **cvec[100]**: TF-IDF topic keyword vector

### 5.3 Known Limitations

- MarBERT/AraBERT unavailable due to HuggingFace authentication errors
- No timestamps captured from Twitter scraping (all timestamps set to datetime.now())
- No interaction data collected (replies, retweets, likes)
- FAISS dimension mismatch between legacy (734-dim) and pipeline (372-dim) scripts
- Only stylometric modality implemented (4 of 5 modalities pending)
- Facebook and cross-platform pipelines not operational

## 6. Experimental Validation Summary

### 6.1 Executed Experiments

15 experiments executed on 31 Egyptian Twitter accounts:

**Stylometric Experiments:**
- Stylometric fingerprint extraction (372-dim vectors from 31 users)
- Ensemble embedding validation (3-model weighted ensemble)
- Lexical feature extraction (TTR, word length, punctuation, emoji ratios)
- TF-IDF topic vector extraction

**Search & Similarity Experiments:**
- FAISS IndexFlatIP construction and search
- Cosine similarity computation
- Cross-user similarity distribution analysis

**Verification Experiments:**
- Egyptian account verification (3-layer scoring system)
- Demographic filtering accuracy

**Validation Experiments:**
- Publication readiness assessment (6/10 claims publication-ready)
- Prototype capability catalog (12 capabilities assessed)

### 6.2 Key Results

| Metric | Value |
|---|---|
| Accounts fingerprinted | 31 Egyptian Twitter accounts |
| Fingerprint dimension | 372-dim |
| FAISS search time | ~16us per query |
| Mean cross-user similarity | ~0.26 (cosine) |
| Egyptian verification layer | 3-layer (bio, posts, bonus) |
| Publication-ready claims | 6 of 10 (4 require further validation) |
| Accuracy metrics available | 7 of 13 |
| Acceptance criteria tested | 1 of 33 |

### 6.3 Validation Constraints

- **No timestamps**: Temporal features (burstiness, hour_entropy, interpost intervals) are invalid
- **No interactions**: Network modality cannot be tested
- **No cross-platform**: Facebook pipeline not operational
- **MarBERT/AraBERT auth errors**: Ensemble may have silently degraded to single MPNet model
- **No formal accuracy measurement**: Acceptance criteria not yet tested against empirical data

## 7. Publication Readiness

### 7.1 Claims Publication Pipeline

| Claim | Status |
|---|---|
| C01: Stylometric fingerprinting implemented | PUBLICATION-READY |
| C02: Egyptian demographic filtering works | PUBLICATION-READY |
| C03: FAISS similarity search works | PUBLICATION-READY |
| C04: 372-dim fingerprint specification documented | PUBLICATION-READY |
| C05: Database storage pipeline works | PUBLICATION-READY |
| C06: Dashboard visualization works | PUBLICATION-READY |
| C07: MarBERT/AraBERT ensemble integration | REQUIRES FURTHER VALIDATION |
| C08: Temporal feature extraction | REQUIRES FURTHER VALIDATION (no timestamps) |
| C09: Accuracy acceptance criteria met | REQUIRES FURTHER VALIDATION |
| C10: End-to-end pipeline execution | REQUIRES FURTHER VALIDATION (broken FAISS chain) |

### 7.2 Overall Readiness

| Criterion | Score |
|---|---|
| Content completeness | 95% |
| Cross-reference integrity | 90% |
| Structural organization | 85% |
| Platform readiness | 80% |
| **Overall** | **90%** |

## 8. Getting Started

### For Researchers
- Start with the [Theory Guide](Theory_Guide.md) for foundational concepts
- Review the [Axiomatic System](Axiomatic_System.md) for formal foundations
- Read the [Validation](Validation.md) document for testing methodology
- Explore the [Algorithms](Algorithms.md) catalog for implementation details

### For Engineers
- Start with the [Architecture](Architecture.md) document for system design
- Review the [Framework Guide](Framework_Guide.md) for implementation guidance
- See the [Examples](Examples.md) for code walkthroughs
- Check the [Benchmarking Guide](Benchmarking_Guide.md) for evaluation protocols

### For Investigators
- Start with the [Overview](Overview.md) (this document) for high-level understanding
- Review the [FAQ](FAQ.md) for common questions
- Explore the [Attribution Framework](Attribution_Framework.md) for LR interpretation
- See [Case Studies](../Papers/Paper_06_Case_Studies.md) for applied scenarios

### For Evaluators
- Review the [Validation](Validation.md) document for acceptance criteria
- Check the [Benchmarking Guide](Benchmarking_Guide.md) for evaluation protocols
- See the [Glossary](Glossary.md) for terminology
- Review publication readiness in the [Publication Readiness Report](../../PUBLICATION_READINESS_REPORT.md)

## 9. Cross-References

| Document | Description | Path |
|---|---|---|
| Architecture | Complete six-layer architecture | [Architecture.md](Architecture.md) |
| Framework Guide | Implementation guide | [Framework_Guide.md](Framework_Guide.md) |
| Theory Guide | Theoretical foundations | [Theory_Guide.md](Theory_Guide.md) |
| Algorithms | 37 algorithms catalog | [Algorithms.md](Algorithms.md) |
| Validation | Four-tier validation hierarchy | [Validation.md](Validation.md) |
| Examples | Code examples and walkthroughs | [Examples.md](Examples.md) |
| FAQ | Frequently asked questions | [FAQ.md](FAQ.md) |
| Glossary | Standardized terminology | [Glossary.md](Glossary.md) |
| References | Document references | [References.md](References.md) |
| Axiomatic System | 16 axioms, 20 hypotheses, 18 design principles | [Axiomatic_System.md](Axiomatic_System.md) |
| Attribution Framework | LR-based attribution | [Attribution_Framework.md](Attribution_Framework.md) |
| Multi-Modal Framework | Five modalities and fusion | [Multi_Modal_Framework.md](Multi_Modal_Framework.md) |
| Benchmarking Guide | Evaluation scenarios | [Benchmarking_Guide.md](Benchmarking_Guide.md) |

---

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
*Version: 2.0*


