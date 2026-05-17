# Release Manifest — Qwen Accelerator (public release candidate)

> Single source of truth for what this release folder contains and what
> it deliberately does **not** contain.

## Release identity

| Field | Value |
|---|---|
| Product name | Qwen Accelerator |
| Runtime / package name | QwenGhostDomain runtime |
| Release date | 2026-05-17 |
| Target platform | Windows 11, NVIDIA 8 GB VRAM-class GPU |
| Publication status | Prepared for GitHub release |

## Files included in this folder

| File | Role |
|---|---|
| `anima-run.exe` | the CLI binary |
| `README.md` | how to install and use |
| `EXECUTIVE_SUMMARY.md` | one-page outcome summary |
| `LIMITATIONS.md` | honest boundaries |
| `Paper_16_Qwen36_Laptop_Demo.tex` | technical note (LaTeX source) |
| `Paper_16_Qwen36_Laptop_Demo.pdf` | technical note PDF (present only if the build host had a LaTeX toolchain) |
| `RELEASE_MANIFEST.md` | this file |
| `CHECKSUMS.txt` | SHA-256 of every release file (except itself) |

## Files explicitly NOT included

| Item | Why excluded |
|---|---|
| Qwen 3.6 35B-A3B model weights | the user obtains them from the upstream author under that license; we never redistribute the weights |
| Developer-machine per-user data file | per-machine; the user generates their own with `--setup` |
| Developer-machine OS-user-data local state file | per-machine; the user's `--setup` generates their own |
| Developer-machine private inputs tree (sources, dictionaries, build tools) | not for distribution |
| Developer-machine intermediate build artifacts (other than the released binary) | developer-only intermediates |
| Private audit and evidence-pack internals | separate, internal-only |

## What the user must do before the binary runs

1. Obtain the Qwen 3.6 35B-A3B GGUF model file from the upstream author
   under that author's license.
2. Obtain a local OpenAI-compatible inference server binary
   (e.g. `llama-server.exe`). Place on `PATH` or set
   `LLAMA_SERVER_PATH`.
3. Run `anima-run --setup --model <path-to-GGUF>` once on the target
   machine.
4. After setup, use `--prompt`, `--bench`, and `--thinking on|off` as
   described in `README.md`.

## What `--setup` does on the user's machine

- Creates a folder `%APPDATA%\ANIMA\qwen36_accel\` (Windows).
- Writes two small files inside that folder, totalling under 4 KB.
- Does **not** touch the registry.
- Does **not** register an auto-start service.
- Does **not** contact any external network endpoint.
- Does **not** log answers or prompts.
- Is fully reversible by deleting the folder.

## Integrity verification

Every file in this release (except `CHECKSUMS.txt` itself) has a
SHA-256 listed in `CHECKSUMS.txt`. To verify on Windows PowerShell:

```powershell
Get-FileHash .\anima-run.exe -Algorithm SHA256
```

Compare against the matching line in `CHECKSUMS.txt`.

## Out-of-scope claims (please do not infer)

- Not a guarantee that the binary will reach the same throughput on
  hardware other than the one tested. See `LIMITATIONS.md`.
- Not a model-weight redistribution.
- Not a hosted service or cloud inference offering.
- Not a polished consumer product with auto-update.

## Distribution status

This folder is prepared as the public GitHub package for Paper 16.

---

**Prepared:** 2026-05-17
