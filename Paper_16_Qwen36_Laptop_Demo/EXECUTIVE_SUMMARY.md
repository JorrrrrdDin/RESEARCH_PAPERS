# Executive Summary — Qwen Accelerator (public)

> One-page, public-safe summary of what the binary does and what it does not.

## What this is

A local-execution accelerator that lets a user run a **35-billion-parameter MoE language model (Qwen3.6 35B-A3B)** on a **single 8 GB VRAM consumer laptop GPU (RTX 4060 Laptop)** while running the entire serving stack on-device. No external license server. No cloud inference. The user supplies their own model weights from the official upstream; the accelerator does not redistribute them.

## What we proved (local-only, locally measured)

| Claim | Observed |
|---|---|
| User-supplied 35B/3B-active MoE model loads on 8 GB consumer GPU | ✅ |
| 10/10 smoke prompts answered correctly (multi-category, multi-language) | ✅ |
| Decode throughput observed under warm reuse (decode-only timing) | **33–34 tokens/sec** (3-run mean, variance < 4%) |
| Conservative external claim retained | **20+ t/s** (matches earlier F-EXP-A5 evidence 22.7 t/s mean N=2) |
| Tamper detection on the per-user data file | generic reject observed |
| Decoy profile → safe-fail (no crash, no resource exhaustion) | invariant validator rejection observed |
| Per-machine binding of the per-user data file | off-machine load fails by design |
| All work local — no remote upload, no external services | no off-host traffic observed |

## What this is not

- Not a plug-in for any third-party chat application.
- Not a guarantee against an attacker with full local interactive access.
- Not a model-weight redistribution. The user obtains weights from the upstream under the upstream's license.

## Why this matters

- Consumer-laptop LLM acceleration for very large MoE models is a recognized open problem; achieving full-accuracy local execution on 8 GB VRAM addresses it concretely.
- The binary's per-machine binding + safe-fail behavior is observed end-to-end on the test machine.

## Honest limitations

See [LIMITATIONS.md](LIMITATIONS.md).

## Distribution status

No public upload. Any external citation should treat the numbers above as observed-once-locally; broader claims require additional independent reproduction.

---

**Prepared:** 2026-05-17
**Push status:** NOT PUSHED
