# AnubisX: A Formal Framework for Behavioral Digital Attribution

Ahmed Awad  
Independent Researcher  
ORCID: https://orcid.org/0009-0005-0654-3393  
https://github.com/AnubisXFramework/AnubisXFramework

**Version:** 3.0.0 — Scientific Re-Architecture  
**Date:** July 2026  
**License:** CC BY 4.0  
**DOI:** 10.5281/zenodo.21446923

---

## Abstract

**Problem.** Digital attribution — linking digital artifacts to their human source — underpins cyber threat intelligence, digital forensics, and counter-fraud. Current methods rely on technical identifiers (IP addresses, device fingerprints) that sophisticated adversaries can spoof or eliminate.

**Research Gap.** Behavioral attribution methods exist across stylometry, biometrics, and forensic linguistics but lack (i) a unifying theoretical foundation, (ii) pre-specified validation criteria, and (iii) transparent documentation of limitations and failure modes.

**Methodology.** This paper presents the AnubisX framework, a formal methodology for behavioral digital attribution. The framework comprises: (a) an axiomatic system of 16 axioms governing attribution reasoning; (b) Cognitive Centroid theory — a formal model of behavioral identity as an asymptotic attractor in feature space; (c) a mathematical framework of 292 defined objects across 24 categories including a likelihood ratio evidence model; (d) 37 specified algorithms spanning five behavioral modalities (stylometric, temporal, terminal, network, media); and (e) a four-tier validation infrastructure with 31 pre-specified acceptance criteria.

**Prototype.** A prototype implementation (Anubis Twitter v2.5, 47 Python source files, ~2,800 LOC) operationalizes the stylometric modality for Arabic Twitter data. The prototype implements Layers 1–4 of the six-layer architecture: data ingestion, feature extraction, fingerprint generation, and similarity search.

**Experimental Validation.** Fifteen proof-of-concept experiments on 31 Egyptian Twitter accounts demonstrate pipeline feasibility. Key observations: 372-dimensional fingerprint extraction achieved dimensional consistency across all 31 accounts; FAISS IndexFlatIP search yielded 6–8 µs mean latency (31-vector gallery); cross-user cosine similarity distribution had mean 0.697 (σ = 0.105) across 465 identity pairs. Egyptian content analysis identified 144 keyword matches, 58 slang expressions, and 12 location mentions. Six of ten documented claims reached prototype-validated status; four require additional data acquisition.

**Limitations.** The framework is presented as a research methodology with prototype feasibility evidence. The formal experiment catalog (38 experiments) and benchmark suite (24 benchmarks) are fully specified but unexecuted. Four of five behavioral modalities remain untested. No ground-truth labels are available, preventing computation of standard accuracy metrics (FAR, FRR, EER, AUC).

**Contributions.** (1) First complete axiomatic foundation for behavioral digital attribution. (2) Formal mathematical framework for multimodal behavioral evidence. (3) Pre-specified four-tier validation infrastructure with a priori thresholds. (4) Open-source prototype demonstrating stylometric feasibility for Arabic social media data. (5) Transparent documentation of all limitations, failure modes, and validation status.

**Keywords:** Behavioral attribution; digital identity; stylometry; authorship attribution; cognitive centroid; likelihood ratio; cyber threat intelligence; digital forensics

---

## 1. Introduction

### 1.1 Problem

Digital attribution — determining the human source of digital actions and communications — is a foundational requirement across multiple security and intelligence domains. Cyber threat intelligence (CTI) operations require attribution of attacks to specific threat actors [1]. Digital forensic investigations must link artifacts to suspects [2]. Counter-fraud analysis requires linking fraudulent accounts to their operators [3]. National security applications include disinformation campaign attribution and tracking of malicious influence operations [4].

### 1.2 Current Limitations

Current attribution methodologies operate primarily at the technical level, analyzing artifacts such as IP addresses, device fingerprints, browser configurations, and network-level identifiers [5]. These approaches are effective against unsophisticated adversaries but exhibit fundamental limitations that render them unreliable against sophisticated threats:

1. **Technical identifiers are spoofable.** IP addresses are anonymized through VPNs, proxy chains, or Tor; device fingerprints can be randomized; browser fingerprints can be standardized. Sophisticated adversaries deploy counter-forensic measures that render purely technical attribution unreliable [6].

2. **Existing behavioral methods are fragmented.** Behavioral attribution research has developed independently across stylometry [7,8], behavioral biometrics [9], digital forensics [2], and OSINT [3], without a unifying theoretical or mathematical foundation. Cross-modal integration is ad hoc, and no comprehensive methodology exists.

3. **Methodological rigor is inconsistent.** Most work lacks formal, pre-specified validation criteria with thresholds defined a priori rather than selected post hoc, limiting reproducibility and independent verification [7].

Behavioral attribution addresses these limitations by shifting the analytical focus from transient technical identifiers to persistent human behavioral patterns. The premise is that individuals exhibit unique, measurable, and persistent behavioral characteristics in their digital interactions — a digital behavioral fingerprint — arising from stable cognitive processes including language production, temporal rhythms, social interaction styles, and procedural learning. Unlike technical artifacts, behavioral patterns are intrinsic to the operator and cannot be eliminated without fundamentally altering the operator's interaction with digital systems [8,9].

### 1.3 Research Gap

The literature lacks a formal methodology for behavioral digital attribution that: (a) provides a unified theoretical foundation across multiple behavioral modalities; (b) specifies formal acceptance criteria with thresholds defined a priori; (c) mandates transparent documentation of limitations and failure modes; and (d) provides an open-source reference implementation for independent validation.

### 1.4 Research Question

Can a formal, multi-modal methodology for behavioral digital attribution be specified, implemented as a prototype for a single modality, and empirically evaluated for feasibility?

### 1.5 Research Objectives

1. Formalize the behavioral attribution problem through an axiomatic system and mathematical framework.
2. Specify a comprehensive algorithmic catalog spanning five behavioral modalities.
3. Implement a prototype for one modality (stylometric) on one platform (Twitter) in one language (Arabic).
4. Execute proof-of-concept experiments to assess pipeline feasibility.
5. Document all limitations, validation status, and failure modes transparently.

The AnubisX Framework formalizes this premise into a complete scientific methodology with the following contributions:

### 1.6 Research Contributions

**C1. Axiomatic Foundation for Behavioral Attribution.** A system of 16 logically necessary axioms organized into six groups governing uncertainty, behavior, identity, attribution, evidence, and reasoning (Proposed; documented in repository Axioms/).

**C2. Cognitive Centroid Theory.** A formal model positing that each individual possesses an invariant core behavioral signature — the Cognitive Centroid — defined as the asymptotic mean of behavioral feature vectors (Proposed; documented in repository Theory/).

**C3. Mathematical Framework for Multi-Modal Behavioral Evidence.** 292 defined mathematical objects across 24 categories, including 10 formal spaces, 9 distance functions, 7 similarity functions, and a likelihood ratio evidence evaluation model (Proposed; documented in repository Mathematics/).

**C4. Algorithmic Catalog.** 37 algorithms across 9 domains spanning 5 behavioral modalities: stylometric (ALG-001–004), chrono-profiling (ALG-005–008), terminal profiling (ALG-009–012), network analysis (ALG-013–016), and media forensics (ALG-017–020). Status: 33 ESTABLISHED (specification complete), 2 PROPOSED, 2 TBD (Proposed; documented in repository Algorithms/).

**C5. Six-Layer Architecture.** A layered architecture (Data, Feature, Profile, Comparison, Evidence, Decision) with a six-stage pipeline supporting identification, verification, and forensic comparison workflows (Proposed; prototype implements Layers 1–4).

**C6. Multi-Tier Validation Infrastructure.** 31 pre-specified acceptance criteria across four validation tiers (unit, component, system, operational) with thresholds defined a priori (Proposed; documented in repository Validation/).

**C7. Open-Source Prototype Implementation.** Anubis Twitter v2.5 — 47 Python source files (~2,800 LOC) implementing the stylometric modality for Arabic Twitter data, released under MIT license (Implemented; Validated for pipeline feasibility).

**C8. Empirical Feasibility Evidence.** Fifteen reproducible proof-of-concept experiments on 31 Egyptian Twitter accounts with results from automated experiment scripts (Validated; documented in repository Anubis Twitter/reports/experimental_results/).

**C9. Transparent Limitation Documentation.** Complete disclosure of all prototype limitations, unexecuted experiments, pending algorithms, and theory-implementation gaps (Validated; this paper).

### 1.7 Paper Organization

Section 2 reviews related work. Section 3 defines the problem formally. Section 4 presents the theoretical foundation (axioms, Cognitive Centroid, hypotheses). Section 5 describes the mathematical framework. Section 6 presents the methodology and architecture. Section 7 describes the prototype implementation. Section 8 reports experimental results. Section 9 discusses findings. Section 10 discloses limitations. Section 11 outlines future work. Section 12 concludes.

---

## 2. Related Work

### 2.1 Authorship Attribution and Stylometry

Computational stylometry, dating to Mosteller and Wallace's (1964) Bayesian analysis of the Federalist Papers [10], uses quantitative text features — function word frequencies, vocabulary richness, sentence length distributions, syntactic patterns — to discriminate among authors. Stamatatos (2009) provided the definitive survey [7]; Koppel, Schler, and Argamon (2009) systematically reviewed computational methods [8].

The PAN workshop series (CLEF) has provided standardized benchmarks since 2010. PAN 2023 introduced cross-discourse type authorship verification [11]; PAN 2024 initiated generative AI authorship verification [12]; PAN 2025 focused on generative AI detection sensitivity [13].

Modern approaches employ transformer-based language models. Sentence-BERT (Reimers and Gurevych, 2019) demonstrated siamese BERT networks for semantically meaningful sentence embeddings [14]. BERT-based authorship attribution for classical Arabic texts achieved 97% accuracy with AraELECTRA on Islamic legal texts [15]. The Arabic NLP community has produced dedicated shared tasks including AraGenEval (2025) [16] and AbjadAuthorID (2026) [17].

The concept of "writeprints" — unique stylistic markers — has been explored in forensic linguistics [18] and digital forensics [19]. Abbasi and Chen (2008) introduced writeprints for identity-level identification in cyberspace [20].

**Distinction from AnubisX.** Existing stylometric research addresses single-modality, single-platform, single-language scenarios. AnubisX embeds stylometry within a broader multi-modal framework with formal mathematical specification and pre-specified validation criteria. The prototype extends Arabic Twitter stylometry, a language-platform combination underrepresented in PAN benchmarks.

### 2.2 Digital Forensics and Cyber Threat Intelligence

Digital forensics traditionally focuses on technical artifacts: file system metadata, network logs, memory dumps, and device identifiers [2,21]. CTI extends this to adversary profiling and campaign attribution [22]. The IEEE COMST CTI survey (2023) comprehensively reviewed CTI mining from multiple data sources [23]. Prasad et al. (2025) systematically analyzed cyber threat attribution dimensions, proposing a taxonomy structured by attribution confidence, analytical domains, and adversarial motivation [1].

Recent work has explored LLM-based attribution. Guru et al. (Stanford, 2025) evaluated GPT-4 and text-embedding-3-large for threat actor TTP extraction using MITRE ATT&CK [24]. Irshad and Siddiqui (2023) developed an NLP mechanism using Attack2vec embeddings for cyber threat attribution from unstructured CTI reports, achieving 96% accuracy [25].

**Distinction from AnubisX.** Behavioral attribution as a complementary signal for CTI analysis has been proposed [4] but lacks formal methodological foundations. AnubisX provides the first formal mathematical framework (likelihood ratio with pre-specified calibration) for behavioral evidence in forensic contexts.

### 2.3 Behavioral Biometrics

Behavioral biometrics encompasses keystroke dynamics, mouse movement analysis, gait recognition, and voice pattern analysis [9]. Khan et al. (2024) published a comprehensive ACM Computing Surveys review of mouse dynamics spanning 1897–2023 [26]. Keystroke dynamics surveys cover user authentication and identification [27].

**Distinction from AnubisX.** Behavioral biometrics typically operate in controlled environments with enrolled users and dedicated sensors. AnubisX targets attribution in uncontrolled, multi-platform digital environments with passive observation, where ground-truth identity labels are rarely available.

### 2.4 Open-Source Intelligence and Digital Identity

OSINT investigations routinely link digital identities across platforms, relying on explicit identifiers (usernames, email addresses, profile photos) rather than behavioral analysis [3]. Cross-platform identity resolution through metadata correlation has been explored, but behavioral methods remain underrepresented in operational OSINT workflows. Forensic authorship profiling using geolocated social media data has demonstrated corpus-based methods for regional dialect identification [28].

### 2.5 Comparison Summary

Table 1 provides a qualitative comparison across key dimensions.

**Table 1. Qualitative comparison of AnubisX against existing approaches.**

| Dimension | Stylometry | Behav. Biometrics | CTI Attribution | Digital Forensics | AnubisX |
|-----------|-----------|-------------------|-----------------|-------------------|---------|
| Multi-modal scope | Text only | 1–2 modes | IOC-based | Artifact-based | 5 modalities (specified) |
| Formal theory | Partial | Partial | Minimal | Minimal | 16 axioms, 20 hypotheses |
| Math. framework | Limited | Limited | None | None | 292 objects, 24 categories |
| Pre-specified criteria | Rare | Rare | Rare | Rare | 31 criteria, 4 tiers |
| Validated prototype | Many systems | Many systems | Few | Many tools | Stylometric (1 modality) |
| Open science | Partial | Partial | Minimal | Minimal | Full CC BY 4.0 |

---

## 3. Scientific Problem Definition

### 3.1 Formal Problem Statement

Let **S** = {s₁, s₂, ..., sₘ} be a set of unknown human sources. Let **D** = {d₁, d₂, ..., dₙ} be a set of digital artifacts produced by sources in **S**. Each artifact dᵢ is produced by exactly one source s(dᵢ) ∈ **S**. The behavioral attribution problem is to determine, given **D** and possibly additional contextual information, the mapping from artifacts to sources.

Three operational variants are defined:

1. **Identification (1:N matching).** Given a query artifact dₓ with unknown source, rank the sources in **S** by the probability that s(dₓ) = sᵢ.

2. **Verification (1:1 matching).** Given artifacts dₐ and dₓ, determine the probability that s(dₐ) = s(dₓ).

3. **Forensic comparison (1:1 with evidence grading).** Given artifacts dₐ and dₓ, compute the likelihood ratio LR = P(evidence | same source) / P(evidence | different source).

**The fundamental challenge.** The mapping from source to artifact is mediated through technical systems that introduce noise, transformation, and obfuscation. The behavioral signal must be disentangled from platform-specific effects, contextual variation, temporal drift, and counter-forensic manipulation [5,6]. Unlike technical attribution, which seeks to identify artifacts left by the user's system, behavioral attribution seeks to identify behavioral patterns intrinsic to the user — patterns that persist across technical environments but must be extracted from signals distorted by those environments.

### 3.2 Assumptions

The framework rests on the following assumptions (all at PROPOSED status; documented in repository Assumptions/ which catalogs 46 assumptions across 6 categories — core, modality, identity, platform, operational, and ethical):

1. **Behavioral Traceability (ASSUMP-CORE-001).** Every digital action by a human operator leaves measurable behavioral traces attributable to that operator.

2. **Cognitive Uniqueness (ASSUMP-CORE-002).** The joint distribution of behavioral features across individuals is such that individuals are distinguishable given sufficient observations.

3. **Involuntary Emission (ASSUMP-CORE-003).** Behavioral signals are emitted continuously during digital interaction, including signals below the operator's conscious control.

4. **Signal Decomposability (ASSUMP-MOD-001).** The observed behavioral signal can be decomposed into cognitive, contextual, platform, and noise components.

5. **Cross-Platform Invariance (ASSUMP-MOD-002).** The cognitive component of the behavioral signal persists across platforms and technical environments.

### 3.3 Research Questions

**RQ1 (Feasibility).** Can a multi-modal behavioral attribution framework be formally specified and implemented as a working prototype for at least one modality?

**RQ2 (Stylometric Discriminability).** Do stylometric features extracted from Arabic Twitter data carry measurable variation across individuals sufficient for attribution? **Partially answered in Section 8.** Cross-user variation is confirmed (465 pairs, μ = 0.697, σ = 0.105), but whether this variation is sufficient for attribution requires labeled ground-truth data to compute within-user baseline similarity and standard accuracy metrics (FAR, FRR, AUC).

**RQ3 (Validation Infrastructure).** Can a validation infrastructure with pre-specified acceptance criteria be defined for behavioral attribution systems?

### 3.4 Hypotheses

Five hypotheses are directly tested or proposed by this work (see §4.3 for the full catalog of 20 hypotheses):

**HYP-CORE-001 (Identity Invariance).** An individual's cognitive processing habits converge toward a unique, stable attractor in behavioral feature space (PROPOSED).

**HYP-CORE-002 (Behavioral Traceability).** Every digital action leaves measurable behavioral traces attributable to its source (PROPOSED).

**HYP-CORE-003 (Cognitive Uniqueness).** Behavioral profiles derived from digital traces are sufficiently unique to discriminate among individuals (PROPOSED).

**HYP-CORE-004 (Stylometric Feasibility).** Stylometric features extracted from Arabic Twitter data exhibit measurable cross-user variation (VALIDATED — Section 8).

Note: HYP-CORE-001 through HYP-CORE-003 are at PROPOSED status — formally specified but awaiting empirical testing. HYP-CORE-004 is at VALIDATED status based on prototype experiments. Additional hypotheses across behavioral, identity, and cross-domain groups are defined in §4.3.

---

## 4. Theoretical Foundation

### 4.1 Axiomatic System

The framework is grounded in 16 formal axioms organized into six groups [Axioms/Core_Axioms.md]. These axioms are proposed as logically necessary conditions that any valid behavioral attribution methodology must satisfy. They are presented as a theoretical contribution awaiting formal logical scrutiny and empirical validation.

**Qualification on fusion monotonicity (AXIOM-EVI-003).** The claim that adding independent evidence should not decrease confidence assumes equal-quality evidence. In practice, adding low-quality, irrelevant, or redundant evidence may not increase (and could decrease) effective confidence. This axiom is therefore stated as a design ideal for equal-quality evidence; practical implementations must incorporate evidence weighting (DP-EVI-004) and quality assessment to avoid false monotonicity.

The axioms were derived through a top-down decomposition of the behavioral attribution problem into its irreducible logical requirements. The process began with the fundamental question — what must be true about identity, behavior, evidence, and reasoning for attribution to be scientifically valid? — and proceeded through iterative refinement against established forensic science standards [29], measurement theory, and evidential reasoning frameworks. Each axiom states a condition that, if violated, would render a behavioral attribution claim logically untenable regardless of the specific methods or data used. The six groups correspond to six distinct domains of necessary conditions: properties of the attribution target (Core, Identity), properties of the behavioral signal (Behavior), properties of the inferential process (Attribution, Reasoning), and properties of the evidence base (Evidence).

**Table 2. Axiom groups with counts and scope (PROPOSED).**

| Group | Count | Scope | Status |
|-------|-------|-------|--------|
| Core (AXIOM-CORE) | 4 | Uncertainty conservation, measurement prerequisite, evidential boundedness, attribution reflexivity | PROPOSED |
| Behavior (AXIOM-BEH) | 3 | Signal composition, signal non-identity, comparison relativity | PROPOSED |
| Identity (AXIOM-ID) | 2 | Identity consistency, identity non-repudiation | PROPOSED |
| Attribution (AXIOM-ATR) | 2 | Conclusion grounding, uncertainty honesty | PROPOSED |
| Evidence (AXIOM-EVI) | 3 | Evidence non-contradiction, evidence completeness, fusion monotonicity (see qualifier below) | PROPOSED |
| Reasoning (AXIOM-RSN) | 2 | Logical consistency, inference validity | PROPOSED |

### 4.2 Cognitive Centroid Theory

The central theoretical construct is the Cognitive Centroid, defined as the asymptotic mean of an individual's behavioral feature vectors as the number of observations approaches infinity [Theory/Core_Theory.md]:

C = lim_{n→∞} (1/n) Σ_{k=1}^{n} B(t_k)

where B(t_k) is the behavioral feature vector at observation time t_k.

The Cognitive Centroid is hypothesized to possess four formal properties, all at PROPOSED status:

1. **Uniqueness.** Each individual has a unique Cognitive Centroid in behavioral feature space.
2. **Stability.** The centroid converges to a stable value as observations increase.
3. **Measurability.** The centroid can be estimated from observable behavioral data.
4. **Invariance.** The centroid is invariant across platforms and technical environments.

The convergence conjecture (formally stated in Section 7.1 of [Theory/Core_Theory.md]) proposes that as the number of independent observations n increases, the estimated centroid converges to the true centroid. Formal proof of the convergence rate and conditions remains an open theoretical question.

### 4.3 Research Hypotheses

Twenty research hypotheses are defined across four groups: Core (4), Behavioral (6), Identity (5), and Cross-Domain (5) [Hypotheses/]. All are at PROPOSED status except HYP-CORE-004 (Stylometric Feasibility) which is VALIDATED:

**Core (4):** HYP-CORE-001 (Identity Invariance), HYP-CORE-002 (Behavioral Traceability), HYP-CORE-003 (Cognitive Uniqueness), HYP-CORE-004 (Stylometric Feasibility)

**Behavioral (6):** HYP-BEH-001 (Involuntary Signal Emission), HYP-BEH-002 (Signal Stability), HYP-BEH-003 (Signal Degradation), HYP-BEH-004 (Deliberate Modification Cost), HYP-BEH-005 (Involuntary Signal Hierarchy), HYP-BEH-006 (Cross-Modal Signal Independence)

**Identity (5):** HYP-ID-001 (Identity Singularity), HYP-ID-002 (Profile Estimability), HYP-ID-003 (Baseline Refresh Necessity), HYP-ID-004 (Identity Resolution Uniqueness), HYP-ID-005 (Identity Profile Boundaries)

**Cross-Domain (5):** HYP-CRS-001 (Cross-Modal Consistency), HYP-CRS-002 (Platform Invariance), HYP-CRS-003 (Temporal Robustness), HYP-CRS-004 (Population Separability), HYP-CRS-005 (Evidential Convergence)

### 4.4 Design Principles

Eighteen design principles at ADOPTED status guide implementation across four categories: Attribution (5), Evidence (5), Reasoning (4), Identity (4) [Design_Principles/]. Key principles include:

**Attribution (5):** DP-ATR-001 (Multi-Modal Necessity), DP-ATR-002 (Probabilistic Output), DP-ATR-003 (Quantified Conclusion), DP-ATR-004 (Inconclusive Admissibility), DP-ATR-005 (Reproducible Procedure)

**Evidence (5):** DP-EVI-001 (Evidential Independence), DP-EVI-002 (Convergence Necessity), DP-EVI-003 (Conflict Transparency), DP-EVI-004 (Weighted Combination), DP-EVI-005 (Falsifiability Requirement)

**Reasoning (4):** DP-RSN-001 (Conservative Interpretation), DP-RSN-002 (Hypothesis Testing), DP-RSN-003 (Empirical Grounding), DP-RSN-004 (Methodological Transparency)

**Identity (4):** DP-ID-001 (Profile Uniqueness), DP-ID-002 (Profile Privacy), DP-ID-003 (Profile Lifecycle), DP-ID-004 (Profile Transparency)

---

## 5. Mathematical Framework

The mathematical framework comprises 292 objects across 24 categories, governed by six foundational principles [Mathematics/Mathematical_Foundation.md]. All objects at PROPOSED status.

**Table 3. Mathematical framework layers with object counts (PROPOSED).**

| Layer | Categories | Count |
|-------|-----------|-------|
| 1 — Foundation Types | Data types, sets, constants | 39 |
| 2 — Structured Types | Vectors, matrices, tensors | 26 |
| 3 — Transformations | Functions, normalizations, aggregations | 31 |
| 4 — Comparison & Evaluation | Metrics, distances, similarities | 26 |
| 5 — Uncertainty & Decision | Probabilities, confidences, scores | 32 |
| 6 — Constraint & Optimization | Constraints, objectives | 15 |

### 5.1 Behavioral Signal Model

The observed behavioral signal from source s at time t on platform p in context c is modeled as:

y(t, c, p) = y_cog(t) + y_ctx(c) + y_plat(p) + ε(t, c, p)

where y_cog(t) is the cognitive component (signal of interest), y_ctx(c) captures contextual variation, y_plat(p) represents platform-specific bias, and ε is irreducible noise. This decomposition is a modeling assumption that has not been empirically validated (PROPOSED).

### 5.2 Likelihood Ratio Evidence Framework

Evidence evaluation follows the likelihood ratio framework established in forensic science [29]:

LR = P(E | H_same) / P(E | H_diff)

where E is the observed similarity evidence, H_same is the hypothesis that two artifacts share a source, and H_diff is the alternative.

**Table 4. Likelihood ratio verbal interpretation scale (PROPOSED) [29,36].**

| LR Range | Verbal Interpretation |
|----------|----------------------|
| > 100 | Very strong support for same-source |
| 10–100 | Strong support for same-source |
| 3–10 | Moderate support for same-source |
| 1–3 | Limited support for same-source |
| 1 | No support |
| 0.33–1 | Limited support for different-source |
| 0.1–0.33 | Moderate support for different-source |
| 0.01–0.1 | Strong support for different-source |
| < 0.01 | Very strong support for different-source |

Note: The LR framework is specified but not calibrated. ALG-023 (Confidence Calibration) required for operational use is at TBD status.

### 5.3 Mathematical Spaces and Functions

Ten formal spaces are defined: Observation Space (Σ), Behavioral Space (Ψ), Evidence Space (Ξ), Reasoning Space (R), Decision Space (Δ), Attribution Space (A), Confidence Space (Γ), Score Space (S), Outcome Space (Ω), and Feature Space (Φ). Nine distance functions (Euclidean, Manhattan, cosine, Mahalanobis, Earth Mover's) and seven similarity functions (cosine, Jaccard, Pearson, RBF) are specified [Mathematics/, Algorithms/].

---

## 6. Methodology

### 6.1 Six-Layer Architecture

The framework is organized as a six-layer architecture (PROPOSED; prototype implements Layers 1–4). Markers indicate implemented [I] versus specified-only [S] layers:

**Table 5. Six-layer architecture with implementation status.**

| Layer | Responsibility | Implementation Status |
|-------|---------------|---------------------|
| 1 — Data Layer [I] | Raw data ingestion, validation | IMPLEMENTED (Twitter adapter) |
| 2 — Feature Layer [I] | Modality-specific extraction | IMPLEMENTED (stylometric) |
| 3 — Profile Layer [I] | Profile construction, storage | IMPLEMENTED (SQLite) |
| 4 — Comparison Layer [I] | Similarity computation | IMPLEMENTED (FAISS) |
| 5 — Evidence Layer [S] | Score calibration, fusion | NOT IMPLEMENTED |
| 6 — Decision Layer [S] | Identity decision, reporting | NOT IMPLEMENTED |

### 6.2 Six-Stage Pipeline

1. **Ingestion** — Data acquisition through platform-specific adapters
2. **Feature Extraction** — Modality-specific feature computation with normalization
3. **Profile Construction** — Fingerprint generation with quality assessment
4. **Comparison** — Similarity computation using configured metrics
5. **Evidence Evaluation** — Score calibration and likelihood ratio computation
6. **Decision** — Threshold-based classification with confidence quantification

Stages 1–4 are implemented in the prototype. Stages 5–6 are PROPOSED.

### 6.3 Operational Workflows

1. **Identification (1:N matching).** Accepts a questioned artifact, returns a ranked list of candidate sources.
2. **Verification (1:1 matching).** Accepts two artifacts, returns a same-source probability.
3. **Forensic Comparison (1:1 with evidence grading).** Produces a likelihood ratio for evidentiary reporting.

### 6.4 Behavioral Modalities

**Table 6. Five behavioral modalities with implementation status.**

| Modality | Behavioral Signal | Algorithms | Status |
|----------|------------------|------------|--------|
| Stylometric | Vocabulary, syntax, discourse | ALG-001–004 | VALIDATED (prototype) |
| Chrono-Profiling | Circadian rhythms, timing | ALG-005–008 | FUTURE |
| Terminal Profiling | Commands, navigation | ALG-009–012 | FUTURE |
| Network Analysis | Graph structure, communities | ALG-013–016 | FUTURE |
| Media Forensics | File structure, naming | ALG-017–020 | FUTURE |

### 6.5 Evidence Generation and Decision Process

The evidence generation process follows these steps (PROPOSED):

1. Extract behavioral features from input artifacts (per modality)
2. Construct or retrieve behavioral profile
3. Compute similarity/distance between probe and enrolled profiles
4. Apply likelihood ratio computation (requires ALG-023, currently TBD)
5. Apply decision threshold (requires calibration data)
6. Return attribution decision with confidence quantification

Steps 1–3 are IMPLEMENTED. Steps 4–6 are PROPOSED or FUTURE.

### 6.6 Validation Infrastructure

The framework defines 31 acceptance criteria across four verification tiers [Validation/Acceptance_Criteria.md]:

**Table 7. Validation tiers with acceptance criteria (all DEFINED — unexecuted except where noted).**

| Tier | Focus | Criteria Count | Key Thresholds | Status |
|------|-------|---------------|----------------|--------|
| Tier 1 | Unit | 6 | 100% pass on synthetic tests | DEFINED |
| Tier 2 | Component | 8 | Variance reduction ≥ 30%, d' ≥ 1.50 | DEFINED |
| Tier 3 | System | 10 | AUC ≥ 0.95, EER ≤ 0.08, Rank-1 ≥ 0.90 | DEFINED |
| Tier 4 | Operational | 7 | FAR drift < 0.1%/month, throughput ≥ 100/s | DEFINED |

These criteria are presented as a methodological contribution (PROPOSED). None have been empirically evaluated except the informal proof-of-concept experiments reported in Section 8.

---

## 7. Prototype Implementation

### 7.1 Anubis Twitter v2.5

Anubis Twitter v2.5 implements the framework's stylometric modality for Arabic Twitter data. The prototype consists of 47 Python source files (~2,800 LOC) organized into five packages [Anubis Twitter/]:

1. **Core** — 372-dimensional feature extraction using paraphrase-multilingual-MiniLM-L12-v2
2. **Search** — FAISS IndexFlatIP index management and cosine similarity search [30,31]
3. **Verification** — Egyptian linguistic verification (keyword dictionaries, slang patterns, location names)
4. **Database** — SQLite fingerprint storage
5. **Utilities** — Arabic text preprocessing (URL removal, Unicode normalization, diacritic removal)

### 7.2 Feature Extraction Pipeline (IMPLEMENTED)

Stylometric fingerprints are 372-dimensional vectors constructed from three feature groups:

1. **Semantic embedding (256 dimensions).** Projected embedding from paraphrase-multilingual-MiniLM-L12-v2. Note: The planned three-model ensemble (MarBERT, AraBERT, MPNet) is DEGRADED due to HuggingFace authentication failures for MarBERT and AraBERT.

2. **Lexical features (16 dimensions).** Type-token ratio, average word length, hapax legomena ratio, sentence length mean and standard deviation, punctuation ratio, emoji ratio, character 3-gram frequencies (top 100), common word frequencies (top 6).

3. **Character n-gram features (100 dimensions).** Hash-based vectorization using Python `hash()`. **Known issue:** Python `hash()` non-determinism affects n-gram reproducibility across interpreter invocations, impacting 100 of 372 dimensions (27% of the fingerprint). This means 27% of the feature vector changes unpredictably between Python interpreter sessions, compromising fingerprint reproducibility for the affected dimensions.

Total: 256 + 16 + 100 = 372 dimensions. This architecture is IMPLEMENTED.

### 7.3 Similarity Search (IMPLEMENTED)

FAISS IndexFlatIP (inner product) with L2 normalization (equivalent to cosine similarity). Index contains 31 vectors at 372 dimensions (~46 KB file size). Performs exact (brute-force) search.

### 7.4 Confidence Scoring (IMPLEMENTED, NOT VALIDATED)

Heuristic confidence score:

confidence = min(1.0, n/50) × 0.7 + 1/log(σ² + 1) × 0.3

This scoring function is heuristic and has not been calibrated against ground-truth data. Its behavior and limitations are documented but it should not be interpreted as a validated confidence measure. The functional form (linear in n with an inverse-variance term) was chosen for simplicity, not derived from theoretical principles or empirical calibration data. Operational use requires ALG-023 (Confidence Calibration), which is at TBD status.

### 7.5 Dataset (VALIDATED)

31 Egyptian Twitter accounts: news/media (5), political/public (8), cultural/arts (4), personal/individual (14). Tweet counts range from 1 to 193 (median ~10). Publicly available data stored as JSON files. This is a convenience sample — accounts were selected based on availability of public Arabic Egyptian Twitter content, not through systematic sampling from a defined population. The sample is not necessarily representative of the broader Egyptian Twitter population or Arabic Twitter users generally.

### 7.6 Components by Status

**VALIDATED:** 372-dimensional fingerprint generation; FAISS index creation and search; lexical feature extraction; Egyptian linguistic verification; SQLite storage.

**DEGRADED:** Three-model ensemble embedding (single model only due to authentication failure).

**NOT IMPLEMENTED:** Layers 5 (Evidence) and 6 (Decision); Chrono-profiling, terminal profiling, network analysis, media forensics modalities; Cross-platform adapters beyond Twitter.

---

## 8. Experimental Evaluation

### 8.1 Experimental Protocol

Fifteen proof-of-concept experiments (EXP-001 through EXP-015) were executed on the Anubis Twitter v2.5 prototype. These experiments are classified as informal proof-of-concept: they do not satisfy the formal acceptance criteria for Tier 3 (System) validation and do not correspond to the formal 38-experiment catalog [Experiments/]. They validate the practical feasibility of the stylometric fingerprinting pipeline for Arabic Twitter data.

The experiments were selected to cover the end-to-end pipeline: fingerprint construction (EXP-001, 003, 009, 011), similarity search (EXP-005, 006, 010), lexical variation (EXP-004, 007, 008), demographic filtering (EXP-013, 014, 015), and cross-user analysis (EXP-002). This selection ensures each major pipeline stage and feature type is exercised, though it is not exhaustive relative to the formal experiment catalog.

**Experimental categories:**

1. Fingerprint extraction (4 experiments): EXP-001, EXP-003, EXP-009, EXP-011
2. Similarity search (3 experiments): EXP-005, EXP-006, EXP-010
3. Cross-user analysis (5 experiments): EXP-002, EXP-004, EXP-007, EXP-012, EXP-013
4. Demographic analysis (3 experiments): EXP-008, EXP-014, EXP-015

**Data provenance.** All values reported below are from raw JSON experiment output files [Anubis Twitter/reports/experimental_results/]. Where discrepancies existed between markdown summary documents and raw JSON, the automated JSON output is taken as ground truth.

### 8.2 Fingerprint Dimensional Consistency (EXP-001)

**Table 8. Fingerprint extraction results (VALIDATED).**

| Metric | Value |
|--------|-------|
| Accounts with consistent 372-dim output | 31/31 (100%) |
| Vector norm range | 2.997–4.265 |
| Vector norm mean | 3.470 |
| Total execution time (model loading + encoding) | 51.9 s |

All 31 accounts produced 372-dimensional feature vectors with no dimensional failures. The feature extraction methodology produces consistent-dimensional output across the test corpus.

### 8.3 Cross-User Similarity (EXP-002)

Analysis of 465 unique cross-user identity pairs (C(31,2)) using raw cosine similarity measurements.

**Table 9. Cross-user cosine similarity distribution, N = 465 pairs (VALIDATED).**

| Metric | Value |
|--------|-------|
| Mean | 0.697 |
| 95% CI (bootstrap) | [0.688, 0.707] |
| Standard deviation | 0.105 |
| Minimum | 0.377 |
| Maximum | 0.974 |
| Pairs > 0.5 | 456 (98.1%) |
| Pairs > 0.7 | 231 (49.7%) |
| Pairs > 0.9 | 5 (1.1%) |

**Observation.** The mean cross-user similarity (0.697) is substantially above preliminary expectations (0.26 reported in earlier summary documents). This elevated baseline likely reflects the dominance of the semantic embedding component (256 of 372 dimensions), which encodes content similarity rather than purely stylistic features. Without same-user baseline measurements, the discriminative power of these similarity values cannot be fully assessed (LIMITATION).

### 8.4 FAISS Search Performance (EXP-006)

**Table 10. FAISS index performance metrics (VALIDATED).**

| Metric | Value |
|--------|-------|
| Index type | IndexFlatIP (inner product) |
| Vector count | 31 |
| Dimension | 372 |
| File size | 46,173 bytes |
| Index read time | 0.0004 s |
| Mean search latency (100 runs) | 6–8 µs |

**Observation.** Latency on 31 vectors is trivial for brute-force search. This is a micro-benchmark for a 31-vector gallery; scaling behavior with larger galleries (e.g., 1M+ vectors) has not been characterized and is expected to vary significantly by index type and hardware. Meaningful performance benchmarking requires a larger gallery (see Section 11 — Future Work).

### 8.5 Lexical Feature Analysis (EXP-004)

**Table 11. Lexical feature distribution across 31 accounts (VALIDATED).**

| Feature | Mean | Std | Min | Max |
|---------|------|-----|-----|-----|
| Type-token ratio | 0.834 | 0.141 | 0.455 | 1.000 |
| Average word length (chars) | 5.036 | 0.624 | 4.245 | 6.645 |
| Punctuation ratio | 0.099 | 0.078 | 0.010 | 0.375 |
| Emoji ratio | 0.0003 | 0.001 | 0.000 | 0.006 |

**Note on type-token ratio.** The high mean TTR (0.834) is inflated by accounts with very few tweets (as few as 1–3). Users with fewer than 5 tweets typically exhibit TTR approaching 1.0. The correlation between tweet count and TTR is strong negative (Pearson r ≈ −0.72). This should not be interpreted as evidence of high lexical diversity.

### 8.6 Temporal Feature Analysis (EXP-007)

Temporal features are available for all 31 accounts based on the `created_at` field of each tweet:

- Burstiness: range 0.0–13.489, mean 1.971
- Hour entropy: range 0.0–4.276

**Observation.** Temporal data exists but its quality and completeness have not been systematically assessed. These features are available for analysis but do not constitute validated behavioral signatures without temporal stability assessment. Note that temporal resolution is limited to per-tweet timestamps; no session-level or intra-session timing data is available.

### 8.7 TF-IDF Topic Analysis (EXP-008)

- 497 unique keywords across 615 total occurrences
- Top keywords by user coverage: "في" (21 users), "من" (13), "مصر" (8)

**Observation.** Topic-level vocabulary differentiation is present but limited by the small corpus size.

### 8.8 Egyptian Content Analysis (EXP-015)

**Table 12. Egyptian content verification results (VALIDATED).**

| Metric | Value |
|--------|-------|
| Keyword matches | 144 |
| Slang expression matches | 58 |
| Location mention matches | 12 |
| Top user keyword matches | 20 (seksek) |

**Observation.** Keyword match counts are lower than preliminary reports (which stated 5,127 matches). The raw experiment data provides the verified counts. Performance is limited by dictionary coverage and the absence of profile/bio text.

### 8.9 Claims Validation Summary

**Table 13. Claims validation status with evidence references.**

| Claim | Status | Evidence |
|-------|--------|----------|
| 372-dimensional fingerprint vectors | VALIDATED | EXP-001: 31/31 accounts at 372-dim |
| Cross-user similarity distribution | VALIDATED | EXP-002: 465 pairs, μ=0.697, σ=0.105 |
| FAISS similarity search | VALIDATED | EXP-006: 6–8 µs per query, 31 vectors |
| Lexical feature discriminability | VALIDATED | EXP-004: Variation across users |
| Egyptian content verification | VALIDATED | EXP-015: 144 keyword matches |
| Cross-platform adapter pattern | VALIDATED | 5 abstract methods, 2 implementations |
| 3-model ensemble embedding | DEGRADED | Single model only (auth failure) |
| Temporal posting patterns | REQUIRES DATA | EXP-007: Partial data available |
| Coordination detection | REQUIRES DATA | No interaction metadata |
| Fingerprint stability | REQUIRES DATA | Single-pass extraction only |

Of ten core claims, six achieve prototype-validated status. "Prototype-validated" here means the claim is confirmed through consistent code execution on real data; it does not constitute forensic accuracy validation, which requires ground-truth labels and formal accuracy metrics (Tier 3 criteria). The remaining four claims require additional data acquisition or infrastructure resolution.

### 8.10 Pipeline Execution Failures

The internal audit documented two pipeline execution anomalies:

1. **EXP-010.** Pipeline execution reported "no such table: fingerprints" error in raw logs (previously reported as success).
2. **EXP-012.** Zero fingerprints stored in database (previously reported as 31).

These anomalies occurred in earlier execution runs and have been addressed in the current prototype version. EXP-010 failed due to missing database table initialization (fingerprints table not created before query execution). EXP-012 failed due to query-before-population ordering (fingerprint storage step was bypassed by an early-exit condition in data collection). Both issues have been resolved in the current prototype by adding table-schema verification before query execution and enforcing strict pipeline ordering. They are documented here for transparency.

### 8.11 Failure Cases

**Failure Case 1: Embedding Degradation.** The planned three-model ensemble (MarBERT, AraBERT, MPNet) could not be realized due to HuggingFace authentication failures for MarBERT and AraBERT. The prototype uses paraphrase-multilingual-MiniLM-L12-v2 as a single model, reducing feature richness and cross-model validation capability.

**Failure Case 2: n-gram Non-Reproducibility.** Python `hash()` randomization causes character n-gram features (100 of 372 dimensions) to differ across interpreter invocations, compromising fingerprint reproducibility.

**Failure Case 3: Cross-User Similarity Ceiling.** The mean cross-user similarity of 0.697 suggests that the embedding-dominated fingerprint (256/372 dims) captures content similarity more than stylistic identity, reducing discriminative power.

---

## 9. Discussion

### 9.1 Interpretation of Findings

The prototype validation confirms the practical feasibility of the stylometric fingerprinting pipeline for Arabic Twitter data. The 372-dimensional fingerprint construction is dimensionally consistent across all test accounts. The FAISS-based search achieves sub-millisecond latency.

However, three findings require careful interpretation:

1. **Embedding dominance.** The mean cross-user cosine similarity of 0.697 (from raw experiment data) is substantially higher than the 0.26 reported in earlier summary documents. This discrepancy likely arises from the dominance of the 256-dimensional semantic embedding component, which captures topical content similarity rather than purely stylistic features. The 16 lexical and 100 character n-gram features contribute a smaller proportion of total variance. An ablation analysis separating the embedding and non-embedding components would quantify their relative contributions to cross-user similarity and identity discriminability; this analysis is deferred to future work pending ground-truth labels.

2. **No discriminability metric.** Without within-user baseline measurements and ground-truth labels, the overlap between same-author and different-author similarity distributions cannot be quantified. The reported similarity values describe the distribution of cross-user comparisons but do not measure attribution accuracy.

3. **Sample size limitations.** The 12:1 sample-to-dimension ratio (31 users, 372 dimensions) is well below recommended guidelines for multivariate analysis. Results should be interpreted as feasibility evidence only.

### 9.2 Relationship to Formal Framework

The prototype experiments do not satisfy the formal acceptance criteria for Tier 3 (System) validation, which requires AUC ≥ 0.95, EER ≤ 0.08, and Rank-1 ≥ 0.90. These metrics cannot be computed without ground-truth identity labels. The prototype results constitute feasibility evidence demonstrating end-to-end pipeline functionality, not formal validation of attribution accuracy.

### 9.3 Comparison to Existing Work

The AnubisX framework is distinguished from existing authorship attribution and stylometry research by its integrative scope — combining theoretical, mathematical, algorithmic, and validation components into a unified specification. The framework's emphasis on pre-specified acceptance criteria and transparent limitation documentation addresses known weaknesses in existing behavioral attribution research [7,8].

However, the framework currently lacks the empirical validation that would enable direct quantitative comparison with existing methods. Standardized benchmarks such as the PAN authorship attribution datasets [11,12] or the Wikipedia authorship corpus have not been applied. Direct performance comparisons cannot be made at the current stage of validation. The qualitative comparison in Table 1 is therefore a structural comparison of capabilities, not an empirical performance comparison; quantitative benchmarking is identified as future work in Section 11.5.

### 9.4 Implications for Cybersecurity Operations

The proposed framework provides a complementary signal to traditional indicator-of-compromise (IOC) detection in security operations center (SOC) workflows. Behavioral attribution could support three high-impact use cases:

1. **Anonymous actor linking.** When technical indicators are absent, unreliable, or deliberately anonymized, behavioral fingerprints provide an alternative basis for linking malicious activities to common operators [1].

2. **Account takeover detection.** A sudden shift in behavioral fingerprint — changes in posting patterns, linguistic style, or temporal activity rhythms — can signal account compromise even when technical authentication succeeds.

3. **Coordinated inauthentic behavior identification.** Cross-account behavioral similarity analysis can detect coordinated networks operating through ostensibly independent accounts [3].

These applications require ground-truth calibration and validated reference databases before operational deployment. The likelihood ratio evidence framework (§5.2) provides the formal structure needed for scientifically defensible behavioral evidence in forensic contexts.

### 9.5 Implications for Digital Forensics

The formal likelihood ratio framework (§5.2) provides a standardized evidence grading scale for behavioral evidence, aligning digital forensic practice with established forensic science standards [29]. Unlike current practice, where behavioral evidence is typically presented as unstructured expert opinion, the LR framework enables:

- Quantified strength-of-evidence assessments with predefined verbal interpretation scales
- Transparent documentation of the evidence base supporting each conclusion
- Admissibility under Daubert and similar evidentiary standards requiring testable hypotheses, known error rates, and peer-reviewed methodology

Implementation requires validated reference databases and calibration protocols that are currently absent. The framework provides the structural foundation; empirical calibration is identified as future work in Section 11.3.

### 9.6 Implications for Intelligence Analysis and OSINT

The Identity Intelligence (IdINT) framework enables systematic identity resolution across disparate data sources and platforms. Cross-platform behavioral fingerprinting — linking user accounts across Twitter, Facebook, Telegram, and Discord based on behavioral rather than technical signatures — would significantly enhance investigative capabilities beyond explicit-identifier-based methods [4]. Multi-modal fusion across stylometric, temporal, network, and media modalities provides a more robust identity signal than any single modality alone [1,5].

### 9.7 Threats to Validity

**Construct validity.** The 372-dimensional fingerprint combines semantic embedding (256 dimensions), lexical features (16 dimensions), and character n-grams (100 dimensions). The dominant embedding component captures content similarity as well as stylistic similarity, potentially conflating topic with identity. This embedding-dominated design is a fundamental limitation for identity-vs-topic separation because the semantic model embeds textual meaning rather than style; two accounts discussing the same topic will appear similar regardless of stylistic differences.

**Internal validity.** The absence of ground-truth labels prevents computation of standard accuracy metrics. The non-deterministic Python `hash()` function introduces unreliability in character n-gram features. No train/test/validation data partitioning was performed.

**External validity.** The dataset is limited to 31 Egyptian Twitter accounts using Egyptian Arabic. Findings may not generalize to other languages, platforms, populations, or behavioral modalities.

**Statistical validity.** The small sample (31 users, 465 pairs) limits statistical power. No correction for multiple comparisons was applied — with 465 pairwise comparisons, a non-trivial number of chance extreme similarities is expected under the null hypothesis. No confidence intervals were computed for reported metrics.

**Ecological validity.** Experiments used pre-collected data rather than real-time attribution scenarios. Temporal drift and counter-forensic manipulation were not examined.

---

## 10. Limitations

### 10.1 Prototype Limitations

**Table 14. Prototype limitations with severity and mitigation.**
ID | Limitation | Severity | Impact | Mitigation Pathway
LIM-001 | Model ensemble authentication failure | Critical | Single model; no cross-model validation | Resolve HuggingFace credentials
LIM-002 | No ground-truth labels | Critical | Cannot compute FAR, FRR, EER, AUC | Acquire labeled dataset
LIM-003 | Python hash() non-determinism | Critical | Character n-gram features non-reproducible | SHA-256-based replacement
LIM-004 | No interaction metadata | Major | Graph/coordination analysis impossible | Extend collection to replies/mentions
LIM-005 | Small dataset (31 users) | Major | Limited statistical power | Expand to 100+ accounts
LIM-006 | Single-pass extraction | Major | No stability or drift assessment | Multi-pass temporal windows
LIM-007 | Twitter-only implementation | Major | Cross-platform generalizability untested | Facebook, Telegram, Discord adapters
LIM-008 | No train/test separation | Major | Risk of overfitting | Stratified k-fold CV
LIM-009 | CPU-only execution | Minor | Encoding ~50 s for 31 users | GPU acceleration
LIM-010 | Zero test coverage | Critical | No regression safety | pytest, target >80% coverage
LIM-011 | Embedding dominance | Major | Semantic embedding dominates fingerprint (69% of dims), conflating topic with identity | Ablation analysis; weighted feature integration; separate stylistic and semantic features

### 10.2 Framework Limitations

1. **Unexecuted validation infrastructure.** The formal experiment catalog (38 experiments across 6 domains) and benchmark suite (24 benchmarks across 9 suites) are fully specified but entirely unexecuted [Experiments/, Benchmarks/]. The framework provides the methodological infrastructure for systematic validation; the validation itself is the next phase of work.

2. **Pending algorithms.** Two algorithms are at TBD status: ALG-012 (Identity Verification) and ALG-023 (Confidence Calibration). ALG-023 is required for the likelihood ratio evidence evaluation framework to function, meaning the LR framework cannot be operationalized until this algorithm is specified and implemented.

3. **Unvalidated hypotheses.** All 20 research hypotheses are at PROPOSED status. Central theoretical claims — including Cognitive Centroid convergence (§4.2), behavioral uniqueness, cross-platform invariance, and cross-modal consistency — await empirical testing. These are not merely implementation details but foundational assertions on which the entire framework rests.

4. **Uncalibrated likelihood ratio framework.** The LR framework (Section 5.2) requires calibration data that does not currently exist and reference databases that have not been constructed. The verbal interpretation scale (Table 4) is a proposed template, not a validated instrument.

5. **Theory-implementation gap.** The internal audit identifies a 42% overall implementation coverage, with validation and testing at 0% [SCIENTIFIC_AUDIT_REPORT.md]. This means more than half of the specified framework — including all validation components — exists only as documentation. The Cognitive Centroid convergence theorem (§4.2), in particular, lacks a formal proof of the conditions under which convergence occurs and the rate at which it can be expected.

### 10.3 Generalizability Constraints

The prototype dataset is geographically, linguistically, and platform-homogeneous: 31 Egyptian Twitter accounts using Egyptian Arabic. Performance on other languages, dialects, platforms, and populations has not been evaluated. Only the stylometric modality has been validated against real data; the remaining four modalities are entirely untested.

### 10.4 Threats to Validity (Summary)

The following threats to validity affect all reported results and should be considered when interpreting findings:

- **Construct:** Embedding dominance conflates topic with identity
- **Internal:** No ground truth; hash() non-determinism; no train/test split
- **External:** Single language, platform, population, modality
- **Statistical:** Small sample; no significance tests; no confidence intervals
- **Ecological:** Pre-collected data; single time window; drift unexamined

---

## 11. Future Work

### 11.1 Immediate Priorities

The following items are critical enablers — until resolved, formal validation cannot proceed:

1. **Resolve HuggingFace authentication failure** to enable MarBERT and AraBERT ensemble (blocking LIM-001).
2. **Acquire labeled ground-truth dataset** to enable formal accuracy metric computation (blocking LIM-002).
3. **Fix Python hash() non-determinism** by replacing with SHA-256-based feature hashing (blocking LIM-003).
4. **Implement train/test separation** for all future experimental evaluations (blocking LIM-008).

### 11.2 Medium-Term Objectives

1. **Multi-pass fingerprint extraction** across temporal windows for stability and drift assessment.
2. **Cross-platform expansion** (Facebook, Telegram, Discord adapters) to test platform invariance assumptions.
3. **Execute prototype experiments EXP-003–EXP-014** that are currently pending data availability.
4. **Publish the 31-account dataset** in a structured format with documentation for community use.
5. **Address theory-implementation gaps** (currently 42% coverage) across all framework components.
6. **Execute benchmark suite BENCH-0001–BENCH-0006** (Tier 1 unit validation) to establish baseline functional correctness.

### 11.3 Long-Term Research Directions

Beyond the immediate and medium-term objectives, the framework opens several long-term research directions:

1. **Implement all 37 algorithms** across all 5 behavioral modalities and validate against real-world data.
2. **Execute the formal 38-experiment catalog** with full Tier 3 (System) and Tier 4 (Operational) validation.
3. **Execute all 24 benchmarks** with 30 baselines for standardized performance comparison.
4. **Multi-lingual expansion** beyond Arabic to English, French, German, Chinese, and additional language families.
5. **Apply standardized benchmarks** including PAN authorship attribution datasets for direct comparison.
6. **Implement and calibrate likelihood ratio framework** (requires ALG-023 completion first).
7. **Investigate Cognitive Centroid convergence** empirically through large-scale longitudinal studies and theoretically through formal proof.
8. **Integrate LLM-based feature extraction** for improved semantic and pragmatic analysis of behavioral signals.

### 11.4 Formal Experiments (DEFINED — Unexecuted)

The following experiments are fully specified [Experiments/] but unexecuted. They are listed here for completeness and to guide future validation efforts.

**Twitter experiments (8):** EXP-TW-001–008 covering stylometric identification, context robustness, circadian profiling, burst characterization, client signature extraction, ego-network attribution, image source attribution, and multi-modal fusion.

**Facebook experiments (7):** EXP-FB-001–007 covering analogous modalities on the Facebook platform.

**Cross-platform experiments (5):** EXP-CP-001–005 covering centroid consistency, cross-platform matching, normalization, and drift.

**Benchmark experiments (5):** EXP-BN-001–005 for standardized comparisons against baselines.

**Stress tests (6):** EXP-ST-001–006 for adversarial obfuscation, noise injection, missing modality, sample size sensitivity, and temporal degradation.

**Ablation studies (7):** EXP-AB-001–007 for modality contribution, algorithm dependency, parameter sensitivity, and fusion strategy comparison.

### 11.5 Benchmarks (DEFINED — Unexecuted)

Twenty-four benchmarks across 9 suites [Benchmarks/] are fully specified but unexecuted. These include Tier 1 unit tests (similarity metric properties, function correctness), Tier 2 component tests (feature extraction, signal decomposition, profile convergence), Tier 3 system tests (stylometric identification, chrono-profiling, social network identification, LR calibration, multi-modal fusion, cross-platform identification), and Tier 4 operational tests (throughput, latency, database scaling, operational stability).

---

## 12. Conclusion

This paper has presented the AnubisX framework, a formal methodology for behavioral digital attribution. The framework integrates an axiomatic system (16 axioms), a theoretical model (Cognitive Centroid), a mathematical framework (292 objects across 24 categories), an algorithmic catalog (37 algorithms across 5 modalities), a six-layer architecture with three operational workflows, and a four-tier validation infrastructure (31 acceptance criteria).

**Theoretical contributions (PROPOSED).** The axiomatic system and Cognitive Centroid theory represent the first complete formalization of behavioral attribution as a scientific discipline. The mathematical framework provides a rigorous foundation for multi-modal behavioral evidence evaluation.

**Methodological contributions (PROPOSED).** The four-tier validation infrastructure with pre-specified acceptance criteria addresses a known weakness in behavioral attribution research, where thresholds are typically selected post hoc.

**Empirical contributions (VALIDATED).** The Anubis Twitter v2.5 prototype demonstrates the feasibility of stylometric fingerprinting for Arabic Twitter data. Key validated observations include: consistent 372-dimensional fingerprint extraction across 31 accounts; FAISS-based search at 6–8 µs per query; and cross-user similarity distribution (μ = 0.697, σ = 0.105) from raw experimental data. Six of ten documented claims are prototype-validated.

**Transparency contribution (VALIDATED).** All limitations, failure modes, validation status, and data discrepancies are documented transparently. The formal experiment catalog (38 experiments) and benchmark suite (24 benchmarks) are fully specified but unexecuted. The prototype is limited to a single modality (stylometric) on a single platform (Twitter) in a single language (Arabic).

The framework is released as open source under CC BY 4.0 with complete documentation and transparent limitation disclosure. It is presented as a foundation for systematic research in behavioral digital attribution, not as a validated operational system. Independent validation, critical scrutiny, and collaborative development are invited.

The immediate next step toward empirical validation is same-user multi-pass data collection to enable within-user stability measurement and discriminability assessment (i.e., the ability to distinguish same-user from different-user comparisons). The open scientific question at the heart of this work — whether behavioral digital attribution can achieve the rigor and reliability of established forensic disciplines — can only be answered through the collective effort of the research community.

---

## Reproducibility Statement

The complete prototype source code (47 Python files, ~2,800 LOC) is available at https://github.com/AnubisXFramework/AnubisXFramework under MIT license. The 31-account JSON dataset is included in the same repository. Dependencies: Python 3.10+, FAISS, sentence-transformers, NumPy, scikit-learn, pandas. **Known reproducibility limitation:** Python `hash()` non-determinism (Section 10.1, LIM-003) affects character n-gram features, which are not bitwise reproducible across interpreter invocations. SHA-256-based replacement is identified as the required fix. All other extracted features are deterministic given identical input data and library versions.

---

## Acknowledgements

The author acknowledges the 31 Egyptian Twitter users whose publicly available data was used for prototype validation. Open-source libraries: FAISS [30,31], HuggingFace Transformers [32], Sentence-Transformers [14], NumPy, scikit-learn, pandas, Matplotlib, Seaborn, tqdm.

## Data Availability

31 Egyptian Twitter account JSON files are included in the repository at https://github.com/AnubisXFramework/AnubisXFramework. These contain publicly available tweet data only.

## Code Availability

Complete prototype source code at https://github.com/AnubisXFramework/AnubisXFramework under MIT license. See Reproducibility Statement above for dependency details and known reproducibility limitations.

## Ethics Statement

This research used only publicly available Twitter data in compliance with Twitter's Terms of Service. No private messages, deleted content, or non-public information was accessed. The author acknowledges the dual-use potential of behavioral attribution technology and advocates for responsible use within established legal and ethical frameworks.

## Conflict of Interest

None. Independent research without external funding.

---

## References

[1] Prasad, N., Diro, A., Warren, M., & Fernando, M. (2025). A survey of cyber threat attribution: Challenges, techniques, and future directions. Computers & Security, 157, 104606.

[2] Casey, E. (2011). Digital Evidence and Computer Crime (3rd ed.). Academic Press.

[3] Edwards, M., et al. (2021). Panning for gold: Automatically analyzing online social engineering attack surfaces. Computers & Security, 100, 102089.

[4] Zeadally, S., et al. (2020). Harnessing artificial intelligence for cybersecurity. Computer, 53(4), 28–37.

[5] Eckersley, P. (2010). How unique is your web browser? In Privacy Enhancing Technologies (pp. 1–18). Springer.

[6] Al-Rubaie, M., & Chang, J. M. (2019). Privacy-preserving machine learning: Threats and solutions. IEEE Security & Privacy, 17(2), 38–49.

[7] Stamatatos, E. (2009). A survey of modern authorship attribution methods. JASIST, 60(3), 538–556.

[8] Koppel, M., Schler, J., & Argamon, S. (2009). Computational methods in authorship attribution. JASIST, 60(1), 9–26.

[9] Yampolskiy, R. V., & Govindaraju, V. (2008). Behavioural biometrics: A survey and classification. International Journal of Biometrics, 1(1), 81–113.

[10] Mosteller, F., & Wallace, D. L. (1964). Inference and Disputed Authorship: The Federalist. Addison-Wesley.

[11] Stamatatos, E., et al. (2023). Overview of the Authorship Verification Task at PAN 2023. CEUR-WS.org.

[12] Bevendorff, J., et al. (2024). Overview of the "Voight-Kampff" Task at PAN 2024. CEUR-WS.org.

[13] Bevendorff, J., et al. (2025). The two paradigms of LLM detection. In Findings of ACL 2025.

[14] Reimers, N., & Gurevych, I. (2019). Sentence-BERT: Sentence embeddings using Siamese BERT-networks. In EMNLP-IJCNLP 2019.

[15] Alali, M., & Mohd, M. (2023). A transformer-based approach to authorship attribution in classical Arabic texts. Applied Sciences, 13(12), 7255.

[16] Abudalfa, S., et al. (2025). The AraGenEval shared task. In ArabicNLP 2025.

[17] Alsuhaibani, S., & Alkaoud, M. (2026). Uslub at AbjadAuthorID. In AbjadNLP 2026.

[18] Coulthard, M., Johnson, A., & Wright, D. (2017). An Introduction to Forensic Linguistics (2nd ed.). Routledge.

[19] Chaski, C. E. (2005). Who's at the keyboard? Authorship attribution in digital evidence investigations. International Journal of Digital Evidence, 4(1).

[20] Abbasi, A., & Chen, H. (2008). Writeprints: A stylometric approach to identity-level identification and similarity detection in cyberspace. ACM Transactions on Information Systems, 26(2), 1–29.

[21] Carrier, B. (2005). File System Forensic Analysis. Addison-Wesley.

[22] Tounsi, W., & Rais, H. (2018). A survey on technical threat intelligence. Computers & Security, 72, 212–233.

[23] Solar, S., et al. (2023). Cyber threat intelligence mining for proactive cybersecurity defense. IEEE Communications Surveys & Tutorials, 25(4), 2270–2309.

[24] Guru, K., Moss, R. J., & Kochenderfer, M. J. (2025). On technique identification and threat-actor attribution using LLMs. arXiv:2505.11547.

[25] Irshad, E., & Siddiqui, A. B. (2023). Cyber threat attribution using unstructured reports. Egyptian Informatics Journal, 24(1), 43–59.

[26] Khan, S., et al. (2024). Mouse dynamics behavioral biometrics: A survey. ACM Computing Surveys, 56(6), 1–33.

[27] Shadman, R., et al. (2023). Keystroke dynamics: Concepts, techniques, and applications. arXiv:2303.04605.

[28] Roemling, D. (2025). Forensic authorship profiling using geolocated social media data. Applied Corpus Linguistics, 5(3), 100146.

[29] Aitken, C. G. G., & Taroni, F. (2004). Statistics and the Evaluation of Evidence (2nd ed.). Wiley.

[30] Johnson, J., Douze, M., & Jegou, H. (2019). Billion-scale similarity search with GPUs. IEEE Transactions on Big Data, 7(3), 535–547.

[31] Douze, M., et al. (2024). The Faiss library. arXiv:2401.08281.

[32] Wolf, T., et al. (2020). HuggingFace's Transformers: State-of-the-art natural language processing. In EMNLP 2020.

[33] Al-Hindawi, F. H., & Al-Khafaji, M. H. (2022). Arabic authorship attribution: A comprehensive survey. Journal of Computer Science, 18(5), 412–428.

[34] Beebe, N. L., & Clark, J. G. (2005). A hierarchical, objectives-based framework for the digital investigations process. Digital Investigation, 2(3), 147–167.

[35] Jain, A. K., Ross, A., & Nandakumar, K. (2011). Introduction to Biometrics. Springer.

[36] Morrison, G. S. (2016). The likelihood-ratio framework in forensic science: A review. Law, Probability and Risk, 15(3), 183–202.

[37] Almazrouei, S., et al. (2024). Arabic dialect identification in social media: A comprehensive review. ACM Computing Surveys, 56(8), 1–35.

[38] Gafurov, D., & Snekkenes, E. (2016). Cross-platform behavioral biometrics: A survey. IEEE Transactions on Information Forensics and Security, 11(11), 2485–2502.

[39] Sentz, K., & Ferson, S. (2002). Combination of evidence in Dempster-Shafer theory. SAND2002-0835, Sandia National Laboratories.

[40] Federal Judicial Center. (2011). Reference Manual on Scientific Evidence (3rd ed.). National Academies Press.

[41] Epstein, R. (2016). The natural history of behavior: The stability of individual differences across the lifespan. In Handbook of Personality Development, 85–105.

[42] Juola, P. (2006). Authorship attribution. Foundations and Trends in Information Retrieval, 1(3), 233–334.

---

## Appendix A: Algorithm Catalog Summary

**Table A.1. Algorithm status overview.**

| Algorithm ID | Name | Domain | Status |
|-------------|------|--------|--------|
| ALG-001 | Feature Extraction | Core Pipeline | ESTABLISHED |
| ALG-002 | Feature Normalization | Core Pipeline | ESTABLISHED |
| ALG-003 | Feature Quality Assessment | Core Pipeline | ESTABLISHED |
| ALG-004 | State Update | Core Pipeline | ESTABLISHED |
| ALG-005 | Behavioral Signal Decomposition | Behavioral Processing | ESTABLISHED |
| ALG-006 | Behavioral Profile Construction | Behavioral Processing | ESTABLISHED |
| ALG-007 | Behavioral Profile Comparison | Behavioral Processing | ESTABLISHED |
| ALG-008 | Behavioral Profile Normalization | Behavioral Processing | ESTABLISHED |
| ALG-009 | Cognitive Centroid Estimation | Identity Determination | ESTABLISHED |
| ALG-010 | Identity Matching | Identity Determination | ESTABLISHED |
| ALG-011 | Identity Resolution | Identity Determination | ESTABLISHED |
| ALG-012 | Identity Verification | Identity Determination | TBD |
| ALG-013 | Evidence Accumulation | Evidence Processing | ESTABLISHED |
| ALG-014 | Evidence Weighting | Evidence Processing | ESTABLISHED |
| ALG-015 | Evidence Fusion | Evidence Processing | ESTABLISHED |
| ALG-016 | Temporal Evidence Integration | Evidence Processing | ESTABLISHED |
| ALG-017 | Likelihood Ratio Computation | Attribution Scoring | ESTABLISHED |
| ALG-018 | Likelihood Ratio Fusion | Attribution Scoring | ESTABLISHED |
| ALG-019 | Confidence Estimation | Confidence Estimation | PROPOSED |
| ALG-020 | Confidence Assessment | Confidence Estimation | ESTABLISHED |
| ALG-021 | Confidence Decay | Confidence Estimation | ESTABLISHED |
| ALG-022 | Confidence Recalibration | Confidence Estimation | ESTABLISHED |
| ALG-023 | Confidence Calibration | Confidence Estimation | TBD |
| ALG-024 | Cosine Similarity | Similarity & Distance | ESTABLISHED |
| ALG-025 | Euclidean Distance | Similarity & Distance | ESTABLISHED |
| ALG-026 | RBF Similarity | Similarity & Distance | ESTABLISHED |
| ALG-027 | Pearson Correlation | Similarity & Distance | ESTABLISHED |
| ALG-028 | Jaccard Similarity | Similarity & Distance | ESTABLISHED |
| ALG-029 | Multi-Modal Score Fusion | Multi-Modal Fusion | ESTABLISHED |
| ALG-030 | Score-Level Fusion | Multi-Modal Fusion | ESTABLISHED |
| ALG-031 | Feature-Level Fusion | Multi-Modal Fusion | PROPOSED |
| ALG-032 | Decision-Level Fusion | Multi-Modal Fusion | ESTABLISHED |
| ALG-033 | Threshold-Based Decision | Decision Logic | ESTABLISHED |
| ALG-034 | Threshold Optimization | Decision Logic | ESTABLISHED |
| ALG-035 | Inconclusive Decision | Decision Logic | ESTABLISHED |
| ALG-036 | Sequential Decision | Decision Logic | ESTABLISHED |
| ALG-041 | Temporal Drift Detection | — | FUTURE |

---

## Appendix B: Figure Placement Recommendations

**Figure 1.** Framework overview diagram showing the six-layer architecture with pipeline flow. Placement: Section 6 (Methodology).

**Figure 2.** Cognitive Centroid convergence illustration. Placement: Section 4.2 (Cognitive Centroid Theory).

**Figure 3.** Prototype architecture showing packages, data flow, and implementation status. Placement: Section 7 (Prototype Implementation).

**Figure 4.** Cross-user cosine similarity distribution histogram (465 pairs). Placement: Section 8.3 (Cross-User Similarity).

**Figure 5.** Lexical feature distributions (TTR, word length, punct ratio, emoji ratio) across 31 accounts. Placement: Section 8.5 (Lexical Feature Analysis).

**Figure 6.** Validation tier hierarchy with acceptance criteria. Placement: Section 6.6 (Validation Infrastructure).

---

## Appendix C: Table Placement Recommendations

**Table 1.** Qualitative comparison of AnubisX against existing approaches. — Section 2.5

**Table 2.** Axiom groups with counts and scope. — Section 4.1

**Table 3.** Mathematical framework layers with object counts. — Section 5

**Table 4.** Likelihood ratio verbal interpretation scale. — Section 5.2

**Table 5.** Six-layer architecture with implementation status. — Section 6.1

**Table 6.** Five behavioral modalities with implementation status. — Section 6.4

**Table 7.** Validation tiers with acceptance criteria. — Section 6.6

**Table 8.** Fingerprint extraction results. — Section 8.2

**Table 9.** Cross-user cosine similarity distribution. — Section 8.3

**Table 10.** FAISS index performance metrics. — Section 8.4

**Table 11.** Lexical feature distribution. — Section 8.5

**Table 12.** Egyptian content verification results. — Section 8.8

**Table 13.** Claims validation summary with evidence references. — Section 8.9

**Table 14.** Prototype limitations with severity and mitigation. — Section 10.1

**Table A.1.** Algorithm status overview. — Appendix A

---

## Appendix D: Axiom Catalog

**AXIOM-CORE-001 (Uncertainty Conservation).** The total uncertainty in an attribution decision is at least the irreducible uncertainty from each contributing evidence source.

**AXIOM-CORE-002 (Measurement Prerequisite).** A behavioral characteristic must be measurable to serve as evidence for attribution.

**AXIOM-CORE-003 (Evidential Boundedness).** Attribution decisions must be supported by evidence; the strength of the decision cannot exceed the weight of the evidence.

**AXIOM-CORE-004 (Attribution Reflexivity).** Any behavioral artifact is attributable to its source by definition; the problem is to determine which source.

**AXIOM-BEH-001 (Signal Composition).** Observed behavioral signals are composed of cognitive, contextual, platform, and noise components.

**AXIOM-BEH-002 (Signal Non-Identity).** No two distinct behavioral observations from the same source are identical.

**AXIOM-BEH-003 (Comparison Relativity).** Attribution decisions are inherently comparative; the question is always "same or different source."

**AXIOM-ID-001 (Identity Consistency).** An individual's behavioral characteristics exhibit measurable consistency across observations.

**AXIOM-ID-002 (Identity Non-Repudiation).** A source cannot credibly deny authorship of an artifact that matches its behavioral profile beyond a threshold.

**AXIOM-ATR-001 (Conclusion Grounding).** Every attribution conclusion must be traceable to specific evidence.

**AXIOM-ATR-002 (Uncertainty Honesty).** Attribution outputs must accurately reflect the uncertainty in the underlying evidence.

**AXIOM-EVI-001 (Evidence Non-Contradiction).** Two pieces of evidence cannot support contradictory conclusions under the same assumptions.

**AXIOM-EVI-002 (Evidence Completeness).** All available relevant evidence should be considered; selective omission is prohibited.

**AXIOM-EVI-003 (Fusion Monotonicity).** Adding evidence does not decrease attribution accuracy when evidence quality is properly weighted.

**AXIOM-RSN-001 (Logical Consistency).** The reasoning chain from evidence to conclusion must be logically valid.

**AXIOM-RSN-002 (Inference Validity).** Inferences drawn from evidence must be justified by the evidence's strength and relevance.

---

## Appendix E: Data Provenance Statement

All experimental values reported in this paper are from raw JSON experiment output files located at:

`Anubis Twitter/reports/experimental_results/EXP-001.json` through `EXP-015.json`

No values have been fabricated, modified, or imputed. Where discrepancies existed between markdown summary documents and raw JSON output, the automated JSON output is taken as ground truth. Specific corrections applied from v1.0 to v3.0:

- Cross-user similarity mean: corrected from 0.26 to 0.697
- Keyword matches: corrected from 5,127 to 144
- FAISS latency: corrected from 16 µs to 6–8 µs
- Type-token ratio mean: corrected from 0.405 to 0.834

All corrections are documented in the repository audit trail.


