# Paper 15 — LogitFactory: Training-Free Vocabulary Pruning for LLM Inference

**Author:** Myeong Jun Jo · [ORCID: 0009-0006-9540-4666](https://orcid.org/0009-0006-9540-4666)

> Companion to the FIMP framework (Paper 01 onwards). This paper addresses the **logit computation bottleneck** at the LLM's final layer — the single largest discarded computation in modern inference.

---

## TL;DR

Every LLM token requires multiplying the hidden state against the entire output embedding matrix, producing a logit vector of size V where **99.99% of entries are immediately discarded**. LogitFactory prunes the vocabulary *before* the multiplication, achieving **96–100% top-1 accuracy** on GPT-2 with **70–99% FLOP reduction**. In wall-clock terms (pure PyTorch, A100 80GB) the speedup grows monotonically with vocabulary and hidden dimension, reaching **2.59× at V = 500K, d = 16,384**.

---

## The Two Barriers (and Why Nine Years Passed Without Anyone Solving It)

### 1. The Zero-Percent Wall

The intuitive first attempt — cosine similarity between the hidden state and vocabulary cluster centroids — yields **0.0% top-1 accuracy** across every configuration tested. Not low. **Zero.** A researcher seeing this concludes the architecture rejects vocabulary pruning, and stops.

The fix is non-obvious: **dot product on PCA-clustered centroids in the original embedding space** instead of cosine in PCA space. Same data, different geometry. Result: 0% → **96–100%**.

### 2. The Execution Order Trap

A correct implementation written sample-first runs at **0.09× full matmul speed** — slower than the operation it replaces. Inverting the loop to cluster-first (with offline matrix permutation) raises this to **0.86×** without a single algorithmic change. **9.6× process-level improvement.**

Both barriers are independent. Both must be cleared to see any benefit.

---

## Results

### Accuracy (GPT-2 Family)

| Model | Vocab | Hidden | Top-1 | FLOP Saving |
|-------|-------|--------|-------|-------------|
| GPT-2 Small | 50,257 | 768 | **100.0%** | 70.8% |
| GPT-2 Medium | 50,257 | 1,024 | **100.0%** | 66.6% |
| GPT-2 Large | 50,257 | 1,280 | **100.0%** | 66.4% |

Sweep grid: C ∈ {50, 100, 200, 300, 500}, M ∈ {5, 10, 15, 20, 30, 50}.
Sweet spot: C=50–100, M=10–15 → 96–100% accuracy at 70–93% saving.

### Wall-Clock Speedup (A100 80GB, pure PyTorch)

| Scale | V | d | Full (ms) | LogitFactory (ms) | Speedup |
|-------|---|---|-----------|-------------------|---------|
| Qwen-72B class | 152K | 8,192 | 20.04 | 23.34 | 0.86× |
| **GPT-4 class** | **256K** | **12,288** | 49.88 | 45.59 | **1.09×** |
| Ultra | 500K | 12,288 | 97.78 | 49.70 | **1.97×** |
| Mega | 500K | 16,384 | 134.28 | 51.81 | **2.59×** |

The crossover lands inside the current production regime. Speedup grows monotonically with V and d.

### Space-Alignment Ablation

| | Without alignment (cosine) | With alignment (dot + PCA) |
|---|---|---|
| GPT-2 Small | **0.0%** | 96–100% |
| GPT-2 Medium | **0.0%** | 93–100% |
| GPT-2 Large | **0.0%** | 100% |

The projection is a **prerequisite**, not an optimization.

---

## Method Pipeline (4 Stages)

1. **Space Alignment** — dot product on PCA-clustered centroids in original space
2. **Reverse Rotary** — eliminate clusters certainly irrelevant (recall-oriented)
3. **Forward Rotary** — select clusters certainly relevant (precision-oriented)
4. **Precise Computation** — exact logits only on intersection (1–10% of V)

Built-in fallback: if max-softmax < threshold, full computation. Generation quality never below baseline.

---

## Position in the FIMP Series

The FIMP framework starts with memory architecture (Paper 01) and traces a research path through cognition, education, context dynamics, and security:

- **Paper 01** — FIMP: emotion-weighted fractal memory (foundation)
- **Paper 02–11** — graduation theses across 7 disciplines + methodology
- **Paper 12–13** — context pharmacokinetics & pharmacodynamics
- **Paper 14** — GHOST_DOMAIN: privacy-preserving LLM interaction
- **Paper 15 (this)** — **LogitFactory: inference acceleration at the final layer**

Where earlier papers asked *what* an AI should remember and *how* it should reason, Paper 15 asks: *if every step of inference discards 99.99% of its computation, can we prune before the discard?*

The answer, as it turns out, is yes — but only after passing through two failure modes that look insurmountable.

---

## Why It Took Nine Years

The Transformer architecture has been deployed at scale since 2017. The final-layer multiplication has not changed. Yet no one published vocabulary pruning *before* logit computation.

The reason is the Zero-Percent Wall. The most natural first attempt produces 0% accuracy across every configuration a researcher would try. The failure is so complete that it appears to indicate architectural impossibility, not a fixable bug. The space-alignment issue is invisible from inside the failure mode.

The path to the solution in this work was not mathematical intuition. It was **process decomposition** — a technique borrowed from business process engineering. Each pipeline stage (clustering, alignment, scoring, selection, final computation) was examined separately for what it was *actually* doing and what its inputs *required*. Cosine similarity's silent destruction of magnitude information became visible only when scoring was isolated from the surrounding operations.

---

## Companion Material

- **Experimental notebook:** [Kaggle — t028-dual-rotary-experiment](https://www.kaggle.com/code/jomyengjun/t028-dual-rotary-experiment)
- **Author's research index:** [github.com/JorrrrrdDin/RESEARCH_PAPERS](https://github.com/JorrrrrdDin/RESEARCH_PAPERS)
- **Patent filing (KIPO, April 2026):** related work on dual-rotary logit factoring methods (filed)

Implementation details, raw experimental data, and the reference codebase are available on request to the author.

---

## Citation

```bibtex
@article{jo2026logitfactory,
  author = {Myeong Jun Jo},
  title  = {LogitFactory: Training-Free Vocabulary Pruning for Large-Language-Model Inference},
  year   = {2026},
  url    = {https://github.com/JorrrrrdDin/RESEARCH_PAPERS/tree/main/Paper_15_LogitFactory_Vocabulary_Pruning},
  note   = {Paper 15 of the FIMP framework series}
}
```

---

## License

CC BY-NC 4.0 (consistent with parent repository).
