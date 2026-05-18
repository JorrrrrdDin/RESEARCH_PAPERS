# Paper 16 — Rotary GPU

**在消费级 8GB VRAM 设备上本地运行大型 MoE 模型**

🇬🇧 [English](README.md) | 🇰🇷 [한국어](README_KOR.md) | 🇨🇳 中文 (this)

---

**Rotary GPU 不是一个模型。** 它是一个本地执行演示，将大型 MoE 模型带到普通机器上。本文件夹提供了一个公开的验证包，用于在消费级笔记本电脑上运行大型 MoE 语言模型。

随附的演示使用用户自行准备的 Qwen 3.6 系列 35B-A3B MoE GGUF 模型作为其中一个验证目标。**模型权重不包含在内**。要使用此演示，请自行从官方或允许的来源下载验证模型，然后在设置时提供本地模型路径。

## 内容

| 文件 | 用途 |
|---|---|
| `Paper_16_Rotary_GPU_Local_MoE.tex` | 技术注释源代码 |
| `anima-run.exe` | Rotary GPU 演示 CLI 二进制文件 |
| `README.md` | 英文使用指南 |
| `README_KOR.md` | 韩文使用指南 |
| `EXECUTIVE_SUMMARY.md` | 简短公开摘要 |
| `LIMITATIONS.md` | 诚实的边界和硬件警告 |
| `RELEASE_MANIFEST.md` | 发布内容和排除文件 |
| `CHECKSUMS.txt` | SHA-256 校验和 |

## 演示验证内容

- Rotary GPU 本地执行概念
- 用户自行准备的 Qwen 3.6 系列 35B-A3B MoE 模型作为验证目标之一
- 在 8GB VRAM 消费级笔记本电脑 GPU 上本地执行
- Thinking 开/关 用户模式
- 测试环境中内部短烟雾测试集 10/10 通过率
- 保守的公开吞吐量声明: 20+ tokens/s
- 暖启动解码计时观察值超过 30 tokens/s

这是一个验证包，而非模型再分发。

## Rotary GPU 演示运行时

公开包包含 Rotary GPU 演示 CLI (`anima-run.exe`) 及其打包的运行时组件。

运行时组件作为可执行包的一部分包含。**内部实现细节在此公开版本中不予公开**。

## 硬件要求

- Windows 11
- NVIDIA RTX 系列 GPU，VRAM 8GB 或兼容
- 推荐约 32GB 系统 RAM
- 模型文件约需 20GB 可用磁盘空间
- 您自行获取的兼容 GGUF 验证模型文件
- 在 `PATH` 或通过 `LLAMA_SERVER_PATH` 提供的本地 OpenAI 兼容推理服务器二进制文件

## 快速开始

### 1. 准备模型

从官方或允许的来源下载兼容的 GGUF 验证模型。已测试的验证目标是 Qwen 3.6 系列 35B-A3B MoE GGUF 模型。

本地路径示例:

```text
D:\models\Qwen3.6-35B-A3B-Q4_K_M.gguf
```

### 2. 设置

准备本地 OpenAI 兼容推理服务器二进制文件，例如 `llama-server.exe`。将其放在 `PATH` 中，或在运行演示之前将 `LLAMA_SERVER_PATH` 设置为其完整路径。

运行一次设置:

```powershell
.\anima-run.exe --setup --model "D:\models\Qwen3.6-35B-A3B-Q4_K_M.gguf"
```

设置为您的机器准备本地运行时数据。**模型权重不会被本仓库复制或再分发**。

### 3. 运行 prompt

```powershell
.\anima-run.exe --model "D:\models\Qwen3.6-35B-A3B-Q4_K_M.gguf" --prompt "你好" --thinking off
```

### 4. 使用 thinking 模式运行

```powershell
.\anima-run.exe --model "D:\models\Qwen3.6-35B-A3B-Q4_K_M.gguf" --prompt "请逐步思考这个问题。" --thinking on
```

### 5. 运行基准测试

```powershell
.\anima-run.exe --model "D:\models\Qwen3.6-35B-A3B-Q4_K_M.gguf" --bench
```

预期成功的基准测试输出形式:

```text
pass_rate: 1.0
metric_source: timings_api
```

## 不包含内容

本仓库不包含:

- 模型权重
- 训练数据
- 模型再分发
- 内部实现细节
- 私有验证材料
- 私有构建材料

## 备注

首次设置或首次启动服务器可能需要几分钟。本地服务器准备就绪后，后续运行可能会更快。

公开版本仅暴露运行演示所需的最小用户界面。**不公开内部方法**。

## 专利声明

本演示与作者已提交的知识产权方向相关。本仓库作为公开验证包提供，**不作为内部实现细节的公开**。

## 作者

Myeong Jun Jo (조명준)
ORCID: [0009-0006-9540-4666](https://orcid.org/0009-0006-9540-4666)
