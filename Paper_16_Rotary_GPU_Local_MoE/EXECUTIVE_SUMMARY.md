# Executive Summary — Rotary GPU (public)

> One-page, public-safe summary of what the binary does and what it does not.

## What this is

Rotary GPU is a local-execution approach that lets a user run a **35-billion-parameter MoE language model** on a **single 8 GB VRAM consumer laptop GPU (RTX 4060 Laptop)** while running the entire serving stack on-device. No external license server. No cloud inference. In this public validation, the demonstration target is a user-supplied Qwen 3.6-class 35B-A3B GGUF model. The accelerator does not redistribute model weights.

## What we proved (local-only, locally measured)

| Claim | Observed |
|---|---|
| User-supplied 35B/3B-active MoE validation model loads on 8 GB consumer GPU | ✅ |
| 10/10 smoke prompts answered correctly (multi-category, multi-language) | ✅ |
| Decode throughput observed under warm reuse (decode-only timing) | **33–34 tokens/sec** (3-run mean, variance < 4%) |
| Conservative external claim retained | **20+ t/s** (matches earlier F-EXP-A5 evidence 22.7 t/s mean N=2) |
| Public setup flow | one-time local setup, then prompt or benchmark |
| Failure behavior | generic failure only; internal details are not surfaced |
| All work local — no remote upload, no external services | no off-host traffic observed |

## What this is not

- Not a plug-in for any third-party chat application.
- Not a guarantee against an attacker with full local interactive access.
- Not a model-weight redistribution. The user obtains weights from the upstream under the upstream's license.

## Why this matters

- Consumer-laptop LLM acceleration for very large MoE models is a recognized open problem; achieving full-accuracy local execution on 8 GB VRAM addresses it concretely.
- The public package gives a concrete way to reproduce the user-level validation flow without redistributing model weights.

## Honest limitations

See [LIMITATIONS.md](LIMITATIONS.md).

## Distribution status

Public validation package for Paper 16. Any external citation should treat the numbers above as observed-once-locally; broader claims require additional independent reproduction.

---

**Prepared:** 2026-05-17
**Status:** public validation package
