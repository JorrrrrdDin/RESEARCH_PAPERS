# Limitations — public-safe boundaries

> What this binary does NOT do, what it cannot promise, and what remains
> open. Written for a non-developer reader.

## 1. Single hardware target tested

All measurements were taken on one laptop:

- NVIDIA RTX 4060 Laptop, 8 GB VRAM
- Windows 11
- ~32 GB system RAM
- Local NVMe storage

Other 8 GB consumer GPUs (RTX 3060 Laptop, RTX 4060 Desktop, etc.) may
behave differently. The published throughput should not be extrapolated.

## 2. Short-answer benchmark only

The internal benchmark is dominated by short-answer prompts (a few tokens
of output per question). The decode-throughput figure is representative of
short-answer turn-taking. Long-form generation is not yet measured in this
release window.

## 3. Warm reuse vs cold start

The benchmark numbers were measured against an already-warm inference
process — the model was already resident on the GPU when the bench
started. First-run cold start of a multi-GB model from a cold disk cache
can take several minutes. This is a property of the model + storage, not
of this binary.

## 4. No third-party reproduction yet

All measurements were taken by the project owner on the project owner's
machine. Independent reproduction (especially on different 8 GB GPUs)
would strengthen the claim materially.

## 5. Model weights are your responsibility

The binary does not bundle, redistribute, modify, or convert the model
weights. You obtain the Qwen3.6 35B-A3B GGUF file from the upstream
model author under that author's license. License compliance for the
model file is your responsibility.

## 6. No antivirus-style hardening

The binary is intentionally plain — no anti-debug, no anti-VM, no packer.
This is by design: those features cause false-positive antivirus alerts
and erode trust in the artifact. The binary is meant to pass ordinary
endpoint screening.

## 7. Loopback only

All network behavior is loopback only. The binary will refuse to bind to
a non-loopback interface. If you need network exposure, that is a
deliberately unsupported configuration.

## 8. Reasoning quality is the model's, not ours

Answer correctness, reasoning depth, and language coverage are properties
of the Qwen3.6 model. We do not retrain, finetune, or steer the model.
Limitations of the upstream model are inherited by this binary.

## 9. Not a polished consumer product

This is a research-grade evaluation binary. It is not:

- A consumer installer with a GUI.
- A multi-OS distribution (Windows is the only validated target).
- A maintained product with a release cadence.
- A plug-in for any third-party chat application.

## 10. No claim about general-purpose capability

We measured a 10-question short-answer benchmark covering greeting,
arithmetic, translation, code-recall, general-recall, and a compliance
category, in Korean and English. This is a smoke test, not a capability
evaluation. Do not infer general-purpose suitability from it.

---

**Prepared:** 2026-05-17
**Status:** public-safe summary. Detailed internal notes live in the
private audit pack and are not part of this release.
