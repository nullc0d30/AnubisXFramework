# AnubisX Framework — Call for Academic Collaboration

**Date:** 2026-07-15
**Classification:** PUBLIC (C0)
**Platform:** LinkedIn
**Word Count:** ~600
**Audience:** Academic researchers, computational social scientists, NLP researchers

---

**Headline: AnubisX v1.0 — An Open Research Platform for Arabic Behavioral Identity Attribution**

We are releasing the AnubisX Framework v1.0 as an open research platform and invite the academic community to participate in its validation, extension, and application.

## What We're Releasing

The AnubisX Framework is a multi-modal behavioral identity attribution system for Arabic social media text. The v1.0 release includes:

- A complete theoretical specification defining 6 analytical layers, 3 fusion stages, and a cross-platform adaptation architecture
- An operational prototype (Anubis Twitter v2.5) implementing the stylometric modality with validated 372-dimensional fingerprint extraction
- Experimental results from 15 experiments on a dataset of 31 Egyptian Twitter accounts
- Full documentation of capabilities, limitations, and research status

## Invitation for Peer Review

We consider this a living research artifact and actively invite methodological critique. Specific areas where peer review would be most valuable:

1. **Feature engineering decisions** — The choice and implementation of the 372 stylometric features, including lexical weighting schemes, n-gram ranges, and syntactic markers
2. **Similarity metric choice** — We use cosine similarity with raw feature vectors. Alternative metrics (earth mover's distance, information-theoretic divergence) may yield different results
3. **Statistical validation** — Our differentiation claim rests on descriptive statistics from 31 users. Formal hypothesis testing with expanded samples is needed
4. **Dialect analysis methodology** — Our keyword-based Egyptian Arabic detection is a baseline; dialect classification approaches could be compared

## Open Collaboration Areas

### 1. Model Ensemble (Layer 2)
The 3-model fusion layer (stylometric + MarBERT + AraBERT) is defined but blocked. We need collaborators with access to MarBERT/AraBERT weights or alternative Arabic transformer models to implement and evaluate this layer.

### 2. Temporal Analysis (Layer 3)
We require time-stamped data collection — ideally across 4+ weeks — to extract temporal features including posting periodicity, inter-message intervals, and circadian rhythm patterns. Open questions include the stability of temporal features relative to stylometric features.

### 3. Graph Analysis (Layer 4)
Social graph construction from retweet, reply, and mention networks is specified but unimplemented. We seek collaborators working on coordination detection, bot network identification, and graph-based attribution.

### 4. Multi-Platform Evaluation (Layer 6)
The platform adapter architecture is designed for extensibility. We are actively seeking partners to implement adapters for Telegram, Facebook, or other platforms and evaluate cross-platform fingerprint portability.

### 5. Large-Scale Benchmarking
The prototype operates on 31 users. Systematic evaluation at scale (100–10,000 users) with labeled ground truth is the critical path toward forensic application.

## Citation

If you use the AnubisX Framework in your research, please cite:

> AnubisX Framework v1.0: Behavioral Identity Attribution for Arabic Social Media. (2026). [Online]. Available: [GitHub URL]

## Publication Plans

We are targeting the following publication venues and welcome co-authors from the academic community:

- **Journal of Computational Social Science** — Framework design and stylometric validation
- **ACL/WANLP** — Arabic NLP and dialect-specific attribution
- **ASONAM / ICWSM** — Social network analysis and coordination detection
- **Software Architecture Conference** — Modular design patterns for forensic NLP systems

## Get in Touch

Open an issue on GitHub, submit a pull request, or reach out directly. The framework is licensed under CC BY 4.0 — you are free to use, adapt, and build upon it with appropriate attribution.

---

*Science is collaborative. AnubisX is an invitation.*


