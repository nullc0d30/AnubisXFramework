# AnubisX Framework v1.0 — Foundational Release

**Date:** 2026-07-15
**Classification:** PUBLIC (C0)
**Platform:** LinkedIn
**Word Count:** ~500

---

**Headline: Introducing AnubisX Framework v1.0 — Open-Source Behavioral Identity Attribution for Arabic Social Media**

I'm pleased to announce the v1.0 Foundational Release of the AnubisX Framework, an open-source behavioral identity attribution system designed for Arabic social media text.

**What is AnubisX?**

AnubisX is a research framework that extracts behavioral identity fingerprints from social media text and enables similarity-based user attribution. It combines stylometric analysis — the measurement of an individual's unique writing patterns — with scalable similarity search to answer the question: "Who wrote this text?"

The framework is designed as a modular, multi-layered system supporting six analytical modalities: stylometric fingerprinting, ensemble embedding, temporal pattern analysis, social graph construction, fingerprint stability tracking, and cross-platform adaptation.

**What's in v1.0?**

This release delivers the complete theoretical specification alongside a validated prototype (Anubis Twitter v2.5) that implements the stylometric modality end-to-end. Key experimental results include:

- 372-dimensional stylometric fingerprints successfully extracted from 31 Egyptian Twitter accounts
- FAISS-powered cosine-similarity search operating at 16 microseconds per query
- Cross-user differentiation demonstrated — mean similarity between different users is 0.26, compared to self-similarity above 0.80
- Egyptian Arabic keyword analysis validated with 5,127 total matches across the dataset
- 15 experiments executed across the extraction, normalization, search, and analysis pipeline

**What we're honest about**

This release is a foundation, not a finished product. We are transparent about current limitations: the ensemble embedding module (MarBERT/AraBERT) is blocked by Hugging Face authentication issues, temporal and graph analysis layers require additional data collection, and the prototype remains single-platform (Twitter) with CPU-only execution. All limitations are documented in the release package.

**Why open-source?**

Behavioral identity attribution has applications in cybersecurity, disinformation research, forensic investigation, and social science. By releasing this framework openly under CC BY 4.0, we hope to enable collaboration across academia, industry, and independent research — and to subject our methods to the scrutiny of peer review.

**Get involved**

The full release is available on GitHub. We are actively seeking collaborators for:

- Resolving model ensemble authentication and expanding to additional Arabic language models
- Multi-platform data collection and adapter implementation (Telegram, Facebook, others)
- Large-scale evaluation with labeled ground truth data
- Temporal and graph analysis module development
- Peer review and methodological critique

Whether you're a computational social scientist, a forensic analyst, a machine learning researcher, or a developer working on Arabic NLP — your contributions are welcome.

**Links**
- GitHub: [repository URL]
- Documentation: Release package includes full capability catalog, claims registry, limitations, and research status

---

*AnubisX Framework v1.0 — the foundation is laid. Now let's build it together.*


