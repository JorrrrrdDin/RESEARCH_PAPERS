# Paper 02 — Emotion-Weighted Fractal Memory (FIMP)

**A Closed-Loop Architecture for AI Identity Formation through Selective Preservation, Adversarial Verification, and Autonomous Consolidation**

## Author

**Myeong Jun Jo** · [ORCID](https://orcid.org/0009-0006-9540-4666)

## Abstract

Current LLM-based AI systems begin every session from zero — the **Groundhog Day problem**. FIMP solves this with a closed-loop architecture that preserves memories based on *emotional significance* rather than temporal recency, integrating seven subsystems: emotion-weighted selective preservation, three-layer fractal memory hierarchy, multi-agent adversarial verification, structured inter-agent communication, policy-gated governance, autonomous dreaming consolidation, and fractal two-stage recall.

> *AI memory should not be a tape recorder. It should be a heart that remembers what it felt.*

## Key Results

30+ day production deployment · 11 microservices · 1,878 episodes · 105 oracle rules

| Experiment | Key Finding | Verdict |
|------------|-------------|---------|
| Emotion Weight Effect | χ² = 24.387, p < 0.05; dispersion effect | PASS |
| Auto-Promotion Validity | 96.6% valid, mean conf. 0.802 | PASS |
| Temporal Maturation | Stable across Q1–Q4 (ΔW = 0.000) | PASS |
| Self-Diagnosis | 100/100 post-correction pass, risk 0.225 | PASS |
| Communication Efficiency | 23.8% token reduction, < 1ms | PASS |
| Dreaming Consolidation | 3/6 sessions → autonomous safety rule | PASS |

## Architecture

```
┌─────────────────────────────────────────────────────────────────┐
│                     FIMP Closed-Loop Runtime                    │
│                                                                 │
│  ┌──────────┐    ┌──────────┐    ┌──────────┐    ┌──────────┐  │
│  │ Dialogue │───▶│ Observer │───▶│  Debate  │───▶│  Memory  │  │
│  │  Input   │    │ Emotion  │    │  Engine  │    │  Store   │  │
│  └────▲─────┘    │ Analysis │    │ Adv.     │    │ Episode  │  │
│       │          └──────────┘    │ Verify   │    └────┬─────┘  │
│       │                         └──────────┘         │         │
│       │                                              ▼         │
│  ┌────┴─────┐    ┌──────────┐    ┌──────────┐    ┌──────────┐  │
│  │  System  │◀───│  Oracle  │◀───│Governance│◀───│ Pattern  │  │
│  │  Prompt  │    │ Identity │    │ 3-Axis   │    │ Promote  │  │
│  │ Inject   │    │  Rules   │    │  Gate    │    │          │  │
│  └──────────┘    └──────────┘    └──────────┘    └──────────┘  │
│                                                                 │
│  ┌─────────────────────────────────────────────────────────┐    │
│  │              Three-Layer Memory Hierarchy                │    │
│  │                                                         │    │
│  │  Layer 3: Core Identity Kernel     [59 active rules]    │    │
│  │     ▲ promote                          ▼ backprop       │    │
│  │  Layer 2: Episodic Memory         [1,878 episodes]      │    │
│  │     ▲ compress                         ▼ recall         │    │
│  │  Layer 1: Working Memory          [real-time buffer]    │    │
│  └─────────────────────────────────────────────────────────┘    │
│                                                                 │
│  ┌──────────┐    ┌──────────┐    ┌──────────┐                   │
│  │Dreamwalk │    │  Fractal │    │   L2L    │                   │
│  │ Sleep    │    │  Recall  │    │ Protocol │                   │
│  │ Consoli- │    │ Zoom-Out │    │ 23.8%    │                   │
│  │ dation   │    │ Zoom-In  │    │ Token    │                   │
│  │          │    │          │    │ Saving   │                   │
│  └──────────┘    └──────────┘    └──────────┘                   │
│                                                                 │
│  Infrastructure: Gateway · PostgreSQL+pgvector · Redis          │
│  Domain Agents:  Trader · Stock Expert Bot                      │
└─────────────────────────────────────────────────────────────────┘
         11 Docker Compose Microservices · 30+ Days Production
```

## Files

- [`FIMP_v2.tex`](FIMP_v2.tex) — Full paper (LaTeX source)

## Citation

```bibtex
@article{jo2026fimp,
  title   = {Emotion-Weighted Fractal Memory: A Closed-Loop Architecture
             for AI Identity Formation through Selective Preservation,
             Adversarial Verification, and Autonomous Consolidation},
  author  = {Jo, Myeong Jun},
  year    = {2026},
  note    = {ANIMA Research}
}
```
