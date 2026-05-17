# Paper 16 — Rotary GPU

**Local Execution of Large MoE Models on Consumer 8GB VRAM Devices**

This folder provides a public demonstration package for **Rotary GPU**, a local
execution approach for running large MoE language models on consumer
laptop-class machines.

The included validation target is a user-supplied Qwen 3.6-class 35B-A3B MoE
GGUF model. The model weights are **not** included. To use this demo, download
the model yourself from an official or permitted source, then provide the local
model path during setup.

## Contents

| File | Purpose |
|---|---|
| `Paper_16_Rotary_GPU_Local_MoE.tex` | Technical note source |
| `anima-run.exe` | Rotary GPU demo CLI binary |
| `EXECUTIVE_SUMMARY.md` | Short public summary |
| `LIMITATIONS.md` | Honest boundaries and hardware caveats |
| `RELEASE_MANIFEST.md` | Release contents and excluded files |
| `CHECKSUMS.txt` | SHA-256 checksums |

## What This Demonstrates

- Rotary GPU local execution concept
- User-supplied Qwen 3.6-class 35B-A3B MoE model as one validation target
- Local execution on an 8GB VRAM consumer laptop-class GPU
- Thinking on/off user modes
- 10/10 pass rate on the internal short smoke set in the tested environment
- Conservative public throughput statement: 20+ tokens/s
- Warm decode-only timing observed above 30 tokens/s

This is a validation package, not a model redistribution.

## Rotary GPU Demo Runtime

The public package contains the Rotary GPU demo CLI (`anima-run.exe`) and its
packaged runtime component.

The runtime component is included as part of the executable package. Internal
implementation details are not disclosed in this public release.

## Requirements

- Windows 11
- NVIDIA RTX-class GPU with 8GB VRAM or compatible
- About 32GB system RAM recommended
- About 20GB free disk space for the model file
- A Qwen 3.6-class GGUF model file obtained by you
- A local OpenAI-compatible inference server binary available on `PATH` or via
  `LLAMA_SERVER_PATH`

## Quick Start

### 1. Prepare the model

Download a Qwen 3.6-class GGUF model from an official or permitted source.

Example local path:

```text
D:\models\Qwen3.6-35B-A3B-Q4_K_M.gguf
```

### 2. Setup

Run setup once:

```powershell
.\anima-run.exe --setup --model "D:\models\Qwen3.6-35B-A3B-Q4_K_M.gguf"
```

Setup prepares local runtime data for your machine. Model weights are not copied
or redistributed by this repository.

### 3. Run a prompt

```powershell
.\anima-run.exe --model "D:\models\Qwen3.6-35B-A3B-Q4_K_M.gguf" --prompt "Hello" --thinking off
```

### 4. Run with thinking mode

```powershell
.\anima-run.exe --model "D:\models\Qwen3.6-35B-A3B-Q4_K_M.gguf" --prompt "Think through this problem." --thinking on
```

### 5. Run the benchmark

```powershell
.\anima-run.exe --model "D:\models\Qwen3.6-35B-A3B-Q4_K_M.gguf" --bench
```

Expected successful benchmark shape:

```text
pass_rate: 1.0
metric_source: timings_api
```

## What Is Not Included

This repository does not include:

- model weights
- training data
- model redistribution
- internal implementation details
- private validation material
- private build material

## Notes

The first setup or first server start may take several minutes. Later runs may
be faster after the local server is already ready.

The public release exposes the minimum user interface needed to run the demo.
It does not disclose the internal method.

## Patent Notice

This demonstration is related to an already-filed intellectual-property
direction by the author. This repository is provided as a public validation
package, not as a disclosure of internal implementation details.

## Author

Myeong Jun Jo
