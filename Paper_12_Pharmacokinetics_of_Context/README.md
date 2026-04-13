# Paper 12 — Pharmacokinetics of Context

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.19548545.svg)](https://doi.org/10.5281/zenodo.19548545)

**A Dose-Response Framework for Retrieval-Augmented Generation**

## Author

**Myeong Jun Jo** · [ORCID](https://orcid.org/0009-0006-9540-4666)

## Abstract

RAG systems assume more context is better. We prove it wrong.

Context behaves like a drug: too little is useless, too much is toxic, and the therapeutic window is model-specific. In 300 controlled trials across DeepSeek-Chat and Kimi K2.5, we discovered that the same context dose that is medicine for one model is poison for another.

> *The dose makes the poison.* — Paracelsus, 1538

## Key Results

| Metric | DeepSeek-Chat | Kimi K2.5 |
|--------|--------------|-----------|
| Baseline (dose 0) | 19.8/25 | 18.0/25 |
| Peak | **24.9** (dose 8) | **19.2** (dose 2) |
| Collapse | 21.8 (dose 40) | **5.4** (dose 15) |
| Cohen's d (dose 0 vs 8) | **+1.894** | **-3.000** |
| Therapeutic Window | 5–20 episodes | 0–2 episodes |

### ANOVA

| Effect | F | p-value | |
|--------|---|---------|--|
| Model | **312.831** | < 10⁻⁶ | *** |
| Domain | 5.237 | 0.023 | * |
| Dose | 1.103 | 0.355 | ns (Simpson's paradox) |

### Core Discovery

```
DeepSeek:  context = medicine  (broad therapeutic window, d = +1.9)
Kimi:      context = poison    (narrow window, collapses at dose 3, d = -3.0)
Pooled:    dose effect vanishes (opposite slopes cancel = Simpson's paradox)
```

## Experiment

- **300 trials** (2 models × 15 doses × 10 questions)
- **15 dose levels**: 0, 1, 2, 3, 5, 8, 10, 13, 15, 20, 25, 30, 40, 50, 70
- **10 questions**: 5 specialized (domain-specific) + 5 general AI
- **Judge**: DeepSeek-Chat (5 dimensions × 1-5 scale = 25 max)
- **Statistics**: ANOVA, Cohen's d, sigmoid curve fitting (R² = 0.82)

## Files

- [`Paper_12_Pharmacokinetics_of_Context.tex`](Paper_12_Pharmacokinetics_of_Context.tex) — Full paper (LaTeX)

## Citation

```bibtex
@article{jo2026pharmacokinetics,
  title   = {Pharmacokinetics of Context: A Dose-Response Framework
             for Retrieval-Augmented Generation},
  author  = {Jo, Myeong Jun},
  year    = {2026},
  note    = {ANIMA Research}
}
```
