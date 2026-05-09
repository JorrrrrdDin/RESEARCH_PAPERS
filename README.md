# Research Papers

**Myeong Jun Jo** · Independent AI Researcher, South Korea
[ORCID: 0009-0006-9540-4666](https://orcid.org/0009-0006-9540-4666)

---

## Current Work

### LLM Inference Optimization

**Paper 15 — LogitFactory** (May 2026)
*Training-Free Vocabulary Pruning for Large-Language-Model Inference*

- 96–100% top-1 accuracy with 70–99% FLOP reduction on GPT-2 variants
- Resolves the geometric misalignment that caused naive vocabulary pruning to yield 0% accuracy: dot-product on PCA-clustered centroids in original embedding space
- Cluster-first execution: 9.6× wall-clock improvement over functionally identical sample-first implementation
- Pure-PyTorch scaling reaches 2.59× speedup at V=500K, d=16K on A100 80GB
- Patent filed (KIPO, April 2026) · [DOI: 10.5281/zenodo.20098005](https://doi.org/10.5281/zenodo.20098005) · arXiv submission: cs.LG (in preparation)

### AI Security

**Paper 14 — GHOST_DOMAIN** (April 2026)
*Semantic Camouflage for Privacy-Preserving LLM Interaction via Virtual Domain Construction*

- 5-layer protection architecture with information-theoretic security guarantees
- Bounded recovery probability: P(recovery) ≤ K/N under Bayesian-optimal, collusion, and known-plaintext adversary models
- Conditional entropy: H(S|O) ≥ log₂(N/K), view-independent
- Validated across 18 independent experiments (round-trip accuracy 1.000, N up to 512)
- Patent filed (KIPO, April 2026) · arXiv submission: cs.CR (in preparation)

---

## Background: AI Memory Architecture and Cognitive Systems

In early 2026, I developed **FIMP** (Fractal Identity Memory with Multi-agent Protection) — an emotion-weighted memory architecture for persistent AI identity, selective memory, and emotional salience. The system was deployed across 11 microservices for 35+ days, accumulating 3,588+ episodic memories and 115+ self-generated identity rules.

To evaluate whether emotion-weighted memory enables coherent learning across diverse domains, I designed **7 academic curricula** spanning formal reasoning, ethics, humanities, cognitive science, engineering, biology, and AI systems engineering. Each curriculum followed a 6-phase structure (Foundations → Core Methods → Advanced Topics → Specialization → Integration → Capstone), with original reading lists, exercises, and assessments.

ANIMA, the system instantiating FIMP, completed each curriculum and produced a capstone document at the end of each program. These capstones (Papers 02–08) record the resulting outputs. Architectural innovations developed in parallel were excluded from the educational process to isolate the effect of FIMP plus curriculum-based learning.

---

## Repository Structure

```
Paper 01 (FIMP)         Foundation: emotion-weighted memory architecture
                        Author: Myeong Jun Jo

Papers 02–08            Capstone documents from 7 curricula
                        Each addresses a distinct discipline
                        Produced by ANIMA at the end of each program

Paper 09                Convergent Intelligence
                        Category-theoretic synthesis across 7 disciplines

Paper 10                From Demo to Deploy to Grow
                        DDG lifecycle model for self-organizing AI

Paper 11                How to Educate an AI
                        Methodology paper grounded in Bloom, Vygotsky, Ericsson
                        Author: Myeong Jun Jo

Papers 12–13            Pharmacokinetics and Pharmacodynamics of Context
                        Dose-response and resonance models for RAG context

Paper 14                GHOST_DOMAIN (AI security)

Paper 15                LogitFactory (LLM inference optimization)
```

---

## Papers

### LLM Inference Optimization

| # | Title | Summary | Status |
|---|-------|---------|--------|
| 15 | LogitFactory | Training-free vocabulary pruning · 70–99% FLOP reduction | arXiv cs.LG (in preparation) |

### AI Security

| # | Title | Summary | Status |
|---|-------|---------|--------|
| 14 | GHOST_DOMAIN | Information-theoretic privacy for external LLM interaction via domain substitution | arXiv cs.CR (in preparation) |

### AI Memory Architecture and Cognitive Systems

| # | Title | Summary | DOI |
|---|-------|---------|-----|
| 01 | [Emotion-Weighted Fractal Memory (FIMP)](Paper_01_FIMP_Emotion_Weighted_Fractal_Memory/) | Emotion-weighted memory architecture for persistent AI identity | [DOI](https://doi.org/10.5281/zenodo.19491326) |
| 05 | [Distributed Cognition](Paper_05_Distributed_Cognition/) | Multi-agent distributed cognitive architecture | [DOI](https://doi.org/10.5281/zenodo.19517327) |
| 08 | [Four-Cluster Integration Framework](Paper_08_AI_Systems/) | AI systems integration and reliability framework | [DOI](https://doi.org/10.5281/zenodo.19517947) |
| 09 | [Convergent Intelligence](Paper_09_Convergent_Intelligence/) | Category-theoretic synthesis across 7 disciplines | [DOI](https://doi.org/10.5281/zenodo.19518032) |

### AI Education and Curriculum Design

| # | Title | Discipline | DOI |
|---|-------|-----------|-----|
| 02 | [From Plausibility to Permissibility](Paper_02_Plausibility_to_Permissibility/) | Formal Reasoning and Safety | [DOI](https://doi.org/10.5281/zenodo.19516962) |
| 03 | [5-Center Decision Framework](Paper_03_5Center_Framework/) | Ethics and Decision Making | [DOI](https://doi.org/10.5281/zenodo.19508891) |
| 04 | [Computation as Culture](Paper_04_Computation_as_Culture/) | Computational Media and Humanities | [DOI](https://doi.org/10.5281/zenodo.19509059) |
| 06 | [Deploy or Die](Paper_06_Deploy_or_Die/) | Engineering and Deployment | [DOI](https://doi.org/10.5281/zenodo.19517456) |
| 07 | [Grow or Die](Paper_07_Biodesign/) | Biodesign and Adaptation | [DOI](https://doi.org/10.5281/zenodo.19517523) |
| 10 | [From Demo to Deploy to Grow](Paper_10_Demo_Deploy_Grow/) | DDG Lifecycle for Self-Organizing AI | [DOI](https://doi.org/10.5281/zenodo.19518110) |
| 11 | [How to Educate an AI](Paper_11_How_to_Educate_AI/) | Methodology — grounded in Bloom, Vygotsky, Ericsson | [DOI](https://doi.org/10.5281/zenodo.19518129) |

### Context Engineering and RAG Theory

| # | Title | Summary | DOI |
|---|-------|---------|-----|
| 12 | [Pharmacokinetics of Context](Paper_12_Pharmacokinetics_of_Context/) | Dose-response model for RAG context injection | [DOI](https://doi.org/10.5281/zenodo.19548545) |
| 13 | [Pharmacodynamics of Context](Paper_13_Pharmacodynamics_of_Context/) | Resonance monopoly model for context window effects | [DOI](https://doi.org/10.5281/zenodo.19555577) |

---

## About ANIMA

ANIMA is a trust-first AI agent architecture designed to make AI **verifiable, governable, and accountable**.

- Multiple architectural innovations filed as patents (Korea, 2026)
- Coverage: memory governance, adversarial verification, multi-agent orchestration, data security, inference optimization
- Production deployment: 11 microservices, 3,588+ episodic memories, 115+ identity rules

---

*Reference implementations are available upon request. Source code is protected under filed patents.*

## License

Research papers in this repository are licensed under [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/).
