<div align="center">
  <img src="assets/logo.png" alt="open-source-ai-models logo" width="200" />
</div>

# Open Source AI Models

> A curated directory of open-source and open-weight AI models for developers, researchers, and AI builders.

Find the right AI model for coding, OCR, computer vision, image generation, speech, reasoning, RAG, agents, and more — with the parameters, hardware requirements, and license you need to actually decide, not just a link.

This is a **directory**, not an *Awesome List*: every entry lists params, VRAM, context length, license, and best-use-case so you can compare models instead of just discovering them. No minimum star count, no invented numbers — see [Model Selection Criteria](#model-selection-criteria) and [CONTRIBUTING.md](CONTRIBUTING.md).

---

## Contents

- [Featured](#featured)
- [Hardware-Based Recommendations](#hardware-based-recommendations)
- [1. General AI](#1-general-ai)
- [2. Coding](#2-coding)
- [3. Multimodal](#3-multimodal)
- [4. Image Generation](#4-image-generation)
- [5. Image Matting & Background Removal](#5-image-matting--background-removal)
- [6. Audio & Speech](#6-audio--speech)
- [7. Retrieval](#7-retrieval)
- [8. Lightweight & Edge AI](#8-lightweight--edge-ai)
- [9. Document AI (OCR)](#9-document-ai-ocr)
- [How to Choose a Model](#how-to-choose-a-model)
- [Model Selection Criteria](#model-selection-criteria)
- [Contributing](#contributing)
- [License](#license)

Categories without a table yet (Computer Vision, Video, Language, Agents) are defined but don't have a verified entry — see [Contributing](#contributing) if you'd like to add the first one.

---

## Featured

**🏆 Best Overall** — [DeepSeek-V3.1](#1-general-ai): 671B/37B-active MoE, hybrid think/non-think mode, 128K context, commercially usable license. [Mistral Large 3](#1-general-ai) (Apache-2.0, 256K context) is the pick if you need a fully permissive license at similar scale.

**💻 Best Coding Models** — [Qwen3-Coder-480B-A35B-Instruct](#2-coding) for server-scale agentic coding; [Qwen3-Coder-30B-A3B-Instruct](#2-coding) or [Devstral Small 2507](#2-coding) for local/single-GPU agentic use; [Codestral 2](#2-coding) for IDE autocomplete (256K context, Apache-2.0).

**🧠 Best Reasoning Models** — [DeepSeek-R1](#1-general-ai) (MIT, frontier, distillation source), [Qwen3-235B-A22B-Thinking-2507](#1-general-ai) (262K context), [QwQ-32B](#1-general-ai) (single-GPU, ~24 GB Q4).

**👁️ Best Vision-Language Models** — [Gemma 3 27B](#3-multimodal) or [Pixtral-12B-2409](#3-multimodal) (both permissive, commercial-friendly); [InternVL3-78B](#3-multimodal) for SOTA open perception/reasoning; [Molmo-72B](#3-multimodal) for full data+code+weights openness; [Phi-4-multimodal-instruct](#3-multimodal) (MIT) for small tri-modal (text+image+audio) on modest hardware.

**✂️ Best Background Removal Models** — [BiRefNet](#5-image-matting--background-removal) (MIT, highest quality/resolution) for general use; [U2-Net](#5-image-matting--background-removal) family (Apache-2.0) for subject-specific variants (Human, Cloth, Anime via IS-Net); [Silueta](#5-image-matting--background-removal) (~43 MB) when file size matters more than accuracy.

**🎨 Best Image Generation Models** — [FLUX.1 \[schnell\]](#4-image-generation) or [Qwen-Image](#4-image-generation) for commercial use (both Apache-2.0); [FLUX.1 \[dev\]](#4-image-generation) / [Stable Diffusion 3.5 Large](#4-image-generation) for max quality, non-commercial or under-$1M-revenue only; [HunyuanImage 3.0](#4-image-generation) for largest open model (80B/13B active).

**🔎 Best Upscaler Models** — [Real-ESRGAN](#super-resolution--upscaling) (BSD-3-Clause) for general photo/anime-video upscaling; [GFPGAN](#super-resolution--upscaling) (Apache-2.0) to pair with it for face restoration; [SwinIR](#super-resolution--upscaling) (Apache-2.0) for transformer-based SOTA restoration.

**🎙️ Best Speech-to-Text Models** — [Whisper large-v3](#6-audio--speech): Apache-2.0, multilingual, runs on CPU via `whisper.cpp`.

**🗣️ Best Text-to-Speech Models** — [Kokoro-82M](#6-audio--speech) (Apache-2.0, <2 GB, real-time on CPU) for fully commercial use; [F5-TTS](#6-audio--speech) for zero-shot voice cloning (CC-BY-NC-4.0, research only).

**📄 Best OCR Models** — [PaddleOCR-VL](#9-document-ai-ocr) (0.9B, Apache-2.0) and [OvisOCR2](#9-document-ai-ocr) (0.8B, Apache-2.0) for SOTA document parsing at sub-1B size; [GLM-OCR](#9-document-ai-ocr) (0.9B, MIT) for the easiest local/Ollama deployment.

**🔍 Best Retrieval / Embedding Models** — [Qwen3-Embedding-0.6B](#7-retrieval) or [nomic-embed-text-v1.5](#7-retrieval) for fully-permissive lightweight embeddings; [gte-Qwen2-7B-instruct](#7-retrieval) for top MTEB quality; [bge-reranker-v2-m3](#7-retrieval) (Apache-2.0) to rerank retrieved candidates.

**🪶 Best Small Models** — [Phi-4-mini-instruct](#8-lightweight--edge-ai) (3.8B, MIT) for text-only edge; [Gemma 3 270M](#8-lightweight--edge-ai) or [Qwen3-0.6B](#8-lightweight--edge-ai) for sub-1B edge/mobile/browser deployment; [Gemma 3 4B](#8-lightweight--edge-ai) for on-device multimodal.

**🔒 Best for Local / Private AI** — [Qwen3-32B](#1-general-ai) and [Qwen3-Coder-30B-A3B-Instruct](#2-coding): both Apache-2.0, run at ~24 GB VRAM quantized.

---

## Hardware-Based Recommendations

| Tier | Recommended models |
|---|---|
| 🟢 CPU | Whisper large-v3 (via whisper.cpp), BGE-M3, BiRefNet, PaddleOCR-VL, OvisOCR2, GLM-OCR, Kokoro-82M, nomic-embed-text-v1.5, mxbai-embed-large-v1, Gemma 3 270M, SmolLM2-1.7B, Qwen3-0.6B, TinyLlama-1.1B, Real-ESRGAN, GFPGAN, SwinIR |
| 🟢 8 GB VRAM | Qwen3-Embedding-0.6B, Phi-4-mini-instruct, Gemma 3 4B, Qwen2.5-VL-3B-Instruct, Nanonets-OCR-s, Granite-4.1-8B, Seed-Coder-8B-Instruct, CodeGemma 7B, F5-TTS, Llama 3.2 1B, Phi-4-multimodal-instruct |
| 🟢 24 GB VRAM | Qwen3-32B (Q4), QwQ-32B (Q4), ERNIE-4.5-21B-A3B (Q4), Qwen3-Coder-30B-A3B-Instruct (Q4), Devstral Small 2507 (Q4), Qwen2.5-Coder-32B-Instruct (Q4), StarCoder2-15B (Q4), Codestral 2 (Q4), Gemma 3 27B (Q4), Pixtral-12B-2409, gte-Qwen2-7B-instruct, FLUX.1 [dev] (quantized), Qwen-Image (quantized), SDXL 1.0, Stable Diffusion 3.5 Large (quantized) |
| 🟢 48 GB+ VRAM | DeepSeek-V3.1, DeepSeek-R1, Mistral Large 3, Kimi K2 Instruct, Command A+, MiniMax-M2, Qwen3-235B-A22B-Thinking-2507, Llama 4 Scout, Qwen3-Coder-480B-A35B-Instruct, HunyuanImage 3.0, Molmo-72B, InternVL3-78B, Qwen2.5-VL-72B-Instruct *(multi-GPU or aggressive quantization at this tier)* |
| 🍎 Apple Silicon | Whisper large-v3 (MLX/whisper.cpp), Qwen3-32B (MLX/GGUF), Phi-4-mini-instruct (MLX/GGUF), SmolLM2-1.7B, Qwen3-0.6B |

VRAM figures are approximate, quantization-dependent estimates for guidance only — verify against each model's official card before provisioning hardware.

---

## 1. General AI

General-purpose LLMs, reasoning, and instruction-following models.

### General LLM

| Model | Params | Context | VRAM | License | Best For |
|---|---:|---:|---:|---|---|
| [Llama 4 Scout](https://www.llama.com/docs/model-cards-and-prompt-formats/llama4/) | 109B total / 17B active (MoE) | 10M tokens | ~66 GB (int4, active experts) / multi-GPU for full weights | Llama 4 Community License (commercial allowed under 700M MAU) | General LLM, long-context, multimodal (text+image in) |
| [Qwen3-32B](https://huggingface.co/Qwen/Qwen3-32B) | 32B (dense) | 32K native / 131K (YaRN) | ~24 GB (Q4) / ~64 GB (fp16) | Apache-2.0 | General LLM, instruction following, reasoning toggle |
| [DeepSeek-V3.1](https://huggingface.co/deepseek-ai/DeepSeek-V3.1) | 671B total / 37B active (MoE) | 128K | Multi-GPU (>400 GB fp8) | DeepSeek Model License (commercial use allowed) | Reasoning, general LLM, hybrid think/non-think mode |
| [Mistral Large 3](https://docs.mistral.ai/models/model-cards/mistral-large-3-25-12) | 675B total / 41B active (MoE) | 256K | Multi-GPU (>400 GB fp8) | Apache-2.0 | Flagship open-weight general LLM, long-context |
| [Kimi K2 Instruct](https://huggingface.co/moonshotai/Kimi-K2-Instruct) | 1T total / 32B active (MoE) | 128K | Multi-GPU (native INT4, still >500 GB) | Modified MIT (attribution required above 100M MAU / $20M mo. revenue) | Drop-in general-purpose chat + agentic use, no long "thinking" |
| [Command A+](https://docs.cohere.com/docs/command-a-plus) | 218B total / 25B active (MoE) | 128K input / 64K output | 2× H100 (fp8) / 1× B200 | Apache-2.0 | Enterprise agentic + RAG with native citation grounding, 48 languages |
| [ERNIE-4.5-21B-A3B](https://huggingface.co/baidu/ERNIE-4.5-21B-A3B-PT) | 21B total / 3B active (MoE) | 128K | ~16 GB (Q4) | Apache-2.0 | Efficient general LLM on a single mid-range GPU |
| [OLMo 2 32B](https://allenai.org/olmo/release-notes) | 32B (dense) | 4K native / 8K (RoPE-scaled) | ~20 GB (Q4) / ~64 GB (fp16) | Apache-2.0 (weights) / ODC-BY (Dolma 2 data) | Fully open reproducible research (weights + training data + code + checkpoints) |

- **Llama 4 Scout**: MoE with 16 experts; the 10M-token context is Meta's advertised maximum and needs specialized long-context serving. Larger sibling Llama 4 Maverick (400B total / 17B active, 1M context) exists for higher-quality workloads.
- **Qwen3-32B**: part of the Qwen3 dense family (0.6B–32B); larger MoE variants (30B-A3B, 235B-A22B) trade dense simplicity for throughput at similar active-parameter cost.
- **DeepSeek-V3.1**: code released under MIT; model weights follow DeepSeek's own model license. 128K is the documented baseline context; some providers expose up to 163,840 tokens.
- **Mistral Large 3**: Mistral's flagship, trained from scratch (3,000 H200 GPUs); both base and instruct checkpoints are Apache-2.0 — a fully permissive license at this scale is still rare among 600B+ models.
- **Kimi K2 Instruct**: the non-thinking, "reflex-grade" counterpart to Kimi K2 Thinking (see [Reasoning](#reasoning) below) — same 1T/32B-active architecture, tuned for fast drop-in chat/agentic use rather than long chain-of-thought.
- **Command A+**: unifies Cohere's prior Command A, Command A Reasoning, Command A Vision, and Command A Translate models into one checkpoint; notable for native multimodal input and built-in citation/grounding spans. Cohere's earlier Command A/R/R+ models were CC-BY-NC (non-commercial) — Command A+ is Cohere's first entry in this family under a fully permissive Apache-2.0 license.
- **ERNIE-4.5-21B-A3B**: part of Baidu's ERNIE 4.5 family (0.3B–424B, all Apache-2.0); this size is the practical sweet spot for running a modern MoE general LLM on a single consumer GPU.
- **OLMo 2 32B**: Allen Institute for AI's fully open release — unlike the other entries here, it publishes not just weights but the full Dolma 2 pretraining dataset, training code, every intermediate checkpoint, and post-training recipes, at the cost of a much shorter native context window (4K, RoPE-extendable to 8K) than the other models in this table.

### Reasoning

Dedicated reasoning / "thinking" models — trained or tuned for long chain-of-thought before answering (math, logic, science, code).

| Model | Params | Context | VRAM | License | Best For |
|---|---:|---:|---:|---|---|
| [DeepSeek-R1](https://huggingface.co/deepseek-ai/DeepSeek-R1) | 671B total / 37B active (MoE) | 128K | Multi-GPU (>400 GB fp8) | MIT | Frontier open reasoning, distillation source for smaller models |
| [Qwen3-235B-A22B-Thinking-2507](https://huggingface.co/Qwen/Qwen3-235B-A22B-Thinking-2507) | 235B total / 22B active (MoE) | 262K native | Multi-GPU (>120 GB, quantized) | Apache-2.0 | Scaled thinking mode, math/science/coding benchmarks |
| [QwQ-32B](https://huggingface.co/Qwen/QwQ-32B) | 32.5B (dense) | 131K | ~24 GB (Q4) / ~64 GB (fp16) | Apache-2.0 | Reasoning on a single high-end GPU, local/private use |
| [gpt-oss-120b](https://huggingface.co/openai/gpt-oss-120b) | 117B total / 5.1B active (MoE) | 128K | ~80 GB (native MXFP4) / single 80 GB GPU | Apache-2.0 | OpenAI's first open-weight reasoning model, strong tool use |
| [Kimi K2 Thinking](https://huggingface.co/moonshotai/Kimi-K2-Thinking) | 1T total / 32B active (MoE) | 256K (262,144) | Multi-GPU (native INT4, still >500 GB) | Modified MIT (must display "Kimi K2" if >100M MAU or >$20M/mo revenue) | Long-horizon agentic reasoning, hundreds of sequential tool calls |
| [GLM-4.6](https://huggingface.co/zai-org/GLM-4.6) | 355B total (MoE) | 200K input / 128K output | Multi-GPU (>200 GB, quantized) | MIT | Frontier open reasoning + coding + agentic tasks |
| [Magistral Small](https://huggingface.co/mistralai/Magistral-Small-2509) | 24B (dense) | 128K (reliable to ~40K) | ~16 GB (Q4) / ~48 GB (fp16) | Apache-2.0 | Reasoning on a single mid-range GPU, built on Mistral Small 3.2 |

- **DeepSeek-R1**: MIT license explicitly permits distillation and commercialization — the most widely used teacher model for smaller open reasoning models.
- **Qwen3-235B-A22B-Thinking-2507**: the dedicated "thinking" checkpoint of Qwen3-235B-A22B (separate from the default instruct checkpoint). Qwen recommends context well above 131K for long chain-of-thought tasks.
- **gpt-oss-120b**: OpenAI's first open-weight release since GPT-2; uses alternating dense/locally-banded-sparse attention and ships natively in MXFP4, making the 117B-total model fit on a single 80 GB GPU. A smaller sibling, gpt-oss-20b (21B total / 3.6B active), targets ~16 GB VRAM.
- **Kimi K2 Thinking**: interleaves step-by-step reasoning with tool calls across hundreds of turns without drift; ships as native INT4 to keep the 1T-parameter model's memory footprint down. The "Modified MIT" license is permissive but requires visible attribution at very large scale (100M+ MAU or $20M+/month revenue).
- **GLM-4.6**: Zhipu/Z.ai's frontier MoE, expanded from GLM-4.5's 128K to a 200K input context, with explicit improvements to coding, reasoning, long-context, and agentic tool use.
- **Magistral Small**: the only dense, single-GPU-friendly model in this list's upper tier; built on Mistral Small 3.2 with SFT from Magistral Medium reasoning traces plus RL. Its larger sibling, Magistral Medium (~45B), is API-only (not open-weight).
- **QwQ-32B**: dense, built on Qwen2.5 architecture — the best option here for reasoning on a single consumer/prosumer GPU rather than a multi-GPU server. Supersedes an earlier Nov-2024 "Preview" (32K context).

---

## 2. Coding

Code generation, completion, and coding-agent models.

| Model | Params | Context | VRAM | License | Best For |
|---|---:|---:|---:|---|---|
| [Qwen3-Coder-480B-A35B-Instruct](https://huggingface.co/Qwen/Qwen3-Coder-480B-A35B-Instruct) | 480B total / 35B active (MoE) | 256K native / 1M (YaRN) | Multi-GPU (>240 GB, quantized) | Apache-2.0 | Coding agents, repository-scale understanding |
| [Qwen3-Coder-30B-A3B-Instruct](https://huggingface.co/Qwen/Qwen3-Coder-30B-A3B-Instruct) | 30B total / 3B active (MoE) | 256K native / 1M (YaRN) | ~24 GB (Q4) | Apache-2.0 | Local coding agent, single-GPU / high-end consumer setups |
| [MiniMax-M2](https://huggingface.co/MiniMaxAI/MiniMax-M2) | 229.9B total / 9.8B active (MoE) | ~205K | Multi-GPU (>110 GB, quantized) | MIT-style (attribution required above 100M MAU / $30M ARR) | Long-horizon agentic coding, tool-first design |
| [Devstral Small 2507](https://huggingface.co/mistralai/Devstral-Small-2507) | 24B (dense) | 128K | ~16 GB (Q4) / single RTX 4090 or 32 GB Mac | Apache-2.0 | Agentic software-engineering, SWE-bench-tuned local coding agent |
| [Qwen2.5-Coder-32B-Instruct](https://huggingface.co/Qwen/Qwen2.5-Coder-32B-Instruct) | 32.5B (dense) | 32K native / 128K (YaRN) | ~24 GB (Q4) / ~64 GB (fp16) | Apache-2.0 | General code generation/completion, most widely adopted open coding dense model |
| [Codestral 2](https://huggingface.co/mistralai/Codestral-22B-v0.2) | 22B (dense) | 256K | ~16 GB (Q4) / ~44 GB (fp16) | Apache-2.0 (relicensed April 2026; originally Mistral Non-Production) | IDE autocomplete / fill-in-the-middle, 80+ languages |
| [StarCoder2-15B](https://huggingface.co/bigcode/starcoder2-15b) | 15B (dense) | 16K (4K sliding window) | ~10 GB (Q4) / ~32 GB (fp16) | BigCode OpenRAIL-M | Transparent training data (Software Heritage IDs), fill-in-the-middle |
| [Granite-4.1-8B](https://huggingface.co/ibm-granite/granite-4.1-8b) | 8B (dense) | up to 512K | ~6 GB (Q4) / ~16 GB (fp16) | Apache-2.0 | Long-context enterprise coding, RAG, and tool calling |
| [Seed-Coder-8B-Instruct](https://huggingface.co/ByteDance-Seed/Seed-Coder-8B-Instruct) | 8B (dense) | 32K | ~6 GB (Q4) / ~16 GB (fp16) | Apache-2.0 | Lightweight code generation, self-curated training data |
| [CodeGemma 7B](https://huggingface.co/google/codegemma-7b-it) | 7B (dense) | 8K | ~6 GB (Q4) / ~16 GB (fp16) | Gemma Terms of Use (commercial allowed) | Fast code completion on modest hardware |

- Both Qwen3-Coder variants share the same architecture, tuned specifically for agentic coding workflows (tool use, long-context repo understanding) rather than general chat. The 480B model targets server/multi-GPU deployment; 30B-A3B is the practical local/single-GPU choice.
- **MiniMax-M2**: sparse MoE with a "tool-first" design for long-horizon software-engineering and live production troubleshooting; the MIT-style license only requires visible attribution at massive commercial scale (100M+ MAU or $30M+ ARR), otherwise unrestricted.
- **Devstral Small 2507**: built by Mistral AI with All Hands AI specifically for agentic coding; was the #1 open-source model on SWE-bench at release and is light enough for a single RTX 4090 or 32 GB Apple Silicon Mac.
- **Qwen2.5-Coder-32B-Instruct**: the previous-generation Qwen coding model (dense, not MoE) — still one of the most widely fine-tuned and quantized open coding models due to its broad tooling support.
- **Codestral 2**: Mistral's dedicated FIM/autocomplete model; the original 22B (2024) shipped under a non-commercial Mistral license, but was relicensed to Apache-2.0 in April 2026 — verify you're using the relicensed weights before commercial use.
- **StarCoder2-15B**: from the BigCode collaboration (Hugging Face + ServiceNow + NVIDIA); BigCode OpenRAIL-M is an open **responsible-AI license**, not a plain permissive license like Apache/MIT — it includes use-based restrictions, so check the license text for your use case rather than assuming Apache-2.0-equivalent freedom.
- **Granite-4.1-8B**: IBM's long-context dense model (context extendable to 512K), built for instruction following, tool calling, RAG, and coding — notable for enterprise-friendly Apache-2.0 licensing at very long context.
- **Seed-Coder-8B-Instruct**: ByteDance Seed's lightweight code model family (also has -Base and -Reasoning variants, the latter at 64K context); notable for a training pipeline where the model curates its own training data.
- **CodeGemma 7B**: part of the Gemma family, tuned specifically for code completion/chat; smallest context window in this table (8K) but runs comfortably on modest hardware.
- For general-purpose models that also perform reasonably at code (e.g. DeepSeek-V3.1, GLM-4.6), see [General AI](#1-general-ai).

---

## 3. Multimodal

Vision-language and other cross-modal models.

| Model | Params | Context | VRAM | License | Best For |
|---|---:|---:|---:|---|---|
| [Gemma 3 27B](https://huggingface.co/google/gemma-3-27b-it) | 27B | 128K | ~24 GB (Q4) / ~54 GB (fp16) | Gemma Terms of Use (commercial allowed) | Vision-language, multilingual multimodal reasoning |
| [Molmo-72B](https://huggingface.co/allenai/Molmo-72B-0924) | 72B | N/A (not separately documented) | Multi-GPU (>72 GB, quantized) | Apache-2.0 | Fully open VLM — weights + PixMo training data + code all released |
| [InternVL3-78B](https://huggingface.co/OpenGVLab/InternVL3-78B) | 78B | 32K (usable to ~64K) | Multi-GPU (>78 GB, quantized) | Apache-2.0 | SOTA open-source perception + reasoning among open VLMs |
| [Pixtral-12B-2409](https://huggingface.co/mistralai/Pixtral-12B-2409) | 12B + 400M vision encoder | 128K | ~24 GB (fp16) / ~12 GB (quantized) | Apache-2.0 | Natural image + document understanding, variable image resolution |
| [Qwen2.5-VL-72B-Instruct](https://huggingface.co/Qwen/Qwen2.5-VL-72B-Instruct) | 73.4B | 128K (32K native, YaRN-extended) | Multi-GPU (>73 GB, quantized) | Qwen License (commercial allowed; request required above 100M MAU) | Flagship vision-language, document/video/agent understanding |
| [Phi-4-multimodal-instruct](https://huggingface.co/microsoft/Phi-4-multimodal-instruct) | 5.6B | 128K | ~6 GB (Q4) / ~12 GB (fp16) | MIT | Small tri-modal model (text + image + audio in, text out) |

- Gemma 3's 4B, 12B, and 27B variants all accept text + image input with text output; the 1B variant is text-only (see [Lightweight & Edge AI](#8-lightweight--edge-ai)).
- Google's Gemma license is a custom permissive license, not Apache/MIT — classify as **Commercial Allowed**, not plain "Open Source."
- Llama 4 (see [General AI](#1-general-ai)) is also multimodal (text + image in, text out) and can be cross-referenced for larger-scale vision-language needs.
- **Molmo-72B**: Allen Institute for AI's flagship VLM — notable because Ai2 released not just Apache-2.0 weights but the full PixMo training dataset, fine-tuning data, and code, unlike most other entries in this table. A smaller MolmoE-1B (MoE, 1B active/7B total) variant exists for on-device use.
- **InternVL3-78B**: OpenGVLab's "Native Multimodal Pre-Training" model family (also available at 2B/8B/38B); state-of-the-art among open-weight VLMs on several perception/reasoning benchmarks at release, Apache-2.0.
- **Pixtral-12B-2409**: Mistral's first vision-language model; ingests images at their natural resolution/aspect ratio rather than a fixed size, and doesn't trade off text-only benchmark performance to gain vision capability.
- **Qwen2.5-VL-72B-Instruct**: unlike the smaller 3B/7B Qwen2.5-VL sizes (Apache-2.0, see [Document AI](#9-document-ai-ocr)), the 72B carries the custom **Qwen License** — commercial use is allowed, but products/services above 100M monthly active users must request a separate license from Alibaba. Don't assume Apache-2.0 terms carry over from the smaller sizes.
- **Phi-4-multimodal-instruct**: the smallest and only genuinely tri-modal (text+image+audio in) model in this table; MIT-licensed and built on the Phi-4-mini backbone with added vision/speech encoders — a good fit when you need multimodal input on modest hardware rather than frontier-scale VLM quality.

---

## 4. Image Generation

| Model | Params | Task | VRAM | License | Best For |
|---|---:|---|---:|---|---|
| [FLUX.1 \[schnell\]](https://huggingface.co/black-forest-labs/FLUX.1-schnell) | 12B | Text-to-Image | ~16 GB (fp16) / ~8 GB (quantized) | Apache-2.0 | Fast text-to-image generation, commercial use |
| [FLUX.1 \[dev\]](https://huggingface.co/black-forest-labs/FLUX.1-dev) | 12B | Text-to-Image | ~24 GB (fp16) / ~12 GB (quantized) | FLUX.1 [dev] Non-Commercial License | Highest-quality open-weight text-to-image, research/personal use |
| [Qwen-Image](https://huggingface.co/Qwen/Qwen-Image) | 20B (MMDiT) | Text-to-Image | ~24 GB (fp16) / ~12 GB (quantized) | Apache-2.0 | Complex text rendering (Chinese + English), infographics/posters/slides |
| [Stable Diffusion 3.5 Large](https://huggingface.co/stabilityai/stable-diffusion-3.5-large) | 8B | Text-to-Image | ~24 GB (fp16) / ~12 GB (quantized) | Stability AI Community License (free under $1M annual revenue) | General text-to-image, non-commercial or small-business use |
| [HunyuanImage 3.0](https://huggingface.co/tencent/HunyuanImage-3.0) | 80B total / 13B active (MoE) | Text-to-Image | Multi-GPU (>80 GB, quantized) | Tencent Hunyuan Community License (free commercial under 100M MAU) | Largest open text-to-image model, native autoregressive text+image |
| [Stable Diffusion XL (SDXL) 1.0](https://huggingface.co/stabilityai/stable-diffusion-xl-base-1.0) | 3.5B base (6.6B w/ refiner) | Text-to-Image | ~12 GB (fp16) / ~6 GB (quantized) | CreativeML OpenRAIL++-M | Mature ecosystem, 1024×1024 native, widest fine-tune/LoRA support |

- Both FLUX.1 variants share the same 12B-parameter rectified-flow transformer from Black Forest Labs. **schnell** is distilled for few-step (1–4 step) fast inference and is Apache-2.0 (commercial use allowed); **dev** is the higher-fidelity guidance-distilled variant restricted to non-commercial use. Black Forest Labs also offers **FLUX.1 Pro/Flex** (proprietary, API-only) and **FLUX.1 Kontext [dev]** (12B, image editing, same non-commercial license as [dev]).
- Do not describe FLUX.1 [dev] or Stable Diffusion 3.5 as "open source" — both are **Open Weight** with commercial restrictions (revenue thresholds).
- **Qwen-Image**: Alibaba's 20B MMDiT model, notable for commercial-grade Chinese/English text rendering inside generated images (posters, UI mockups, menus). Apache-2.0 and fully open — note this is distinct from the newer Qwen-Image-3.0, which Alibaba has kept closed (no weights released).
- **Stable Diffusion 3.5**: also ships Medium (2.5B) and Large Turbo (distilled, faster) variants under the same Stability AI Community License — free for non-commercial use and for commercial users under $1M annual revenue; enterprise use above that threshold requires contacting Stability AI.
- **HunyuanImage 3.0**: Tencent's native multimodal (unified autoregressive, not diffusion) image generator — the largest openly released text-to-image model by parameter count as of its release. License is free for commercial use up to 100M monthly active users, with attribution required.
- **SDXL 1.0**: still the most widely fine-tuned/LoRA'd open image model due to its age and ecosystem size; CreativeML OpenRAIL++-M is a responsible-AI license (commercial use allowed with use-based restrictions), not a plain permissive license like Apache/MIT.

### Super Resolution / Upscaling

| Model | Size | Task | Hardware | License | Best For |
|---|---:|---|---|---|---|
| [Real-ESRGAN](https://github.com/xinntao/Real-ESRGAN) | ~17–67 MB per variant | Image/Video Super Resolution (2x/4x) | CPU/GPU | BSD-3-Clause | General photo & anime-video upscaling, most widely deployed upscaler |
| [GFPGAN](https://github.com/TencentARC/GFPGAN) | ~340 MB | Face Restoration + Upscaling | CPU/GPU | Apache-2.0 | Restoring/upscaling faces in old or low-quality photos |
| [SwinIR](https://github.com/JingyunLiang/SwinIR) | ~12 MB (small) – ~120 MB (large) | Image Restoration / Super Resolution | CPU/GPU | Apache-2.0 | Transformer-based SOTA restoration (denoising, JPEG artifact removal, SR) |
| [4x-NMKD-Siax-CX](https://openmodeldb.info/models/4x-NMKD-Siax-CX) | ~67 MB | Super Resolution (4x) | CPU/GPU | WTFPL | Clean/lightly-compressed image upscaling (community ESRGAN-arch model) |

- **Real-ESRGAN**: Xintao Wang's official practical extension of ESRGAN; ships several purpose-built variants including `realesrgan-x4plus` (general photo), `realesrgan-x4plus-anime` (illustrations), and `realesr-animevideov3` (anime video, compact architecture) — the exact model names shown in most upscaler apps (Upscayl, chaiNNer, NMKD Video/Image tools). BSD-3-Clause, fully commercial-friendly.
- **GFPGAN**: from the same Tencent ARC lab as Real-ESRGAN and commonly bundled alongside it (Real-ESRGAN upscales the whole image, GFPGAN specifically restores faces) — Apache-2.0, with some third-party components under their own licenses (see repo for details).
- **SwinIR**: academic (CVPR workshop) Swin-Transformer-based restoration model; still a common baseline/comparison point for newer upscalers. Apache-2.0.
- **4x-NMKD-Siax-CX**: one example of the many community-trained ESRGAN-architecture checkpoints on [OpenModelDB](https://openmodeldb.info/) (a community database, not a single organization) — this one is explicitly WTFPL. Many other popular community checkpoints bundled in upscaler apps (e.g. `4xLSDIR`, `4xLSDIRplusC`, `4xHFA2k`, `4xNomos8kSC`, `NMKD-Superscale`) are trained and released by independent contributors (e.g. Philip Hofmann/Phhofm) **without an explicit stated license** in their repos — treat those as **Unknown** and verify directly with the author before commercial redistribution, rather than assuming they're free to use like Real-ESRGAN/GFPGAN/SwinIR above.

---

## 5. Image Matting & Background Removal

Subcategory tree: General · Human/Portrait · Clothing · Animal · Product · Anime/Illustration. Do not assume every segmentation model is a background-removal model — classify by actual intended use.

| Model | Size | Task | Hardware | License | Specialization |
|---|---:|---|---|---|---|
| [BiRefNet](https://github.com/ZhengPeng7/BiRefNet) | ~880 MB (weights) | Dichotomous Image Segmentation / Matting | CPU/GPU | MIT | General |
| [U2-Net](https://github.com/xuebinqin/U-2-Net) | ~176 MB | Salient Object Detection / Matting | CPU/GPU | Apache-2.0 | General |
| [Silueta](https://github.com/danielgatis/rembg) | ~43 MB | Salient Object Detection / Matting | CPU | Unknown (distilled U2-Net variant; `rembg` wrapper itself is MIT) | General, lightweight |
| [U2-Net (Human Segmentation)](https://github.com/xuebinqin/U-2-Net) | ~168 MB | Portrait / Body Segmentation | CPU/GPU | Apache-2.0 | Human / Portrait |
| [U2-Net (Cloth Segmentation)](https://github.com/levindabhi/cloth-segmentation) | ~168 MB | Clothes Parsing (upper/lower/full body) | CPU/GPU | Apache-2.0 (architecture; verify weight release terms in repo) | Clothing |
| [IS-Net (Anime)](https://github.com/xuebinqin/DIS) | ~168 MB | Dichotomous Image Segmentation | CPU/GPU | Apache-2.0 | Anime / Illustration |

- **BiRefNet** ("Bilateral Reference Network") targets high-resolution dichotomous image segmentation and is widely used as the backbone for general-purpose background removal tools (e.g. via `rembg` and `transformers.js`). Released by ZhengPeng7 (CAAI AIR '24 paper) under MIT.
- **U2-Net**: the original nested U-structure salient object detection model (Qin et al., Pattern Recognition 2020), Apache-2.0. Its Human and Cloth segmentation variants above share the same architecture but are fine-tuned for those specific subjects — the Cloth variant in most background-removal apps traces back to Levin Dabhi's community-trained checkpoint rather than the original authors' repo, so double-check that repo's license terms before commercial redistribution.
- **Silueta**: a reduced-size (~43 MB, vs. U2-Net's ~176 MB) general-purpose variant shipped as one of `rembg`'s bundled models; the specific weight license isn't separately documented, so treat it as **Unknown** even though `rembg`'s own code is MIT.
- **IS-Net**: from Xuebin Qin et al.'s "Highly Accurate Dichotomous Image Segmentation" (ECCV 2022, `xuebinqin/DIS`), Apache-2.0; commonly repackaged with anime-tuned weights for illustration/anime subjects.
- Model sizes for the Human/Cloth/Anime variants above reflect the file sizes as packaged in common desktop background-removal apps (e.g. Unbagrnd) — official repos may list slightly different sizes depending on export format.
- Community wrapper projects built on top of any of these models may carry their own separate licenses independent of the model weights; verify the wrapper's license separately if redistributing it.

---

## 6. Audio & Speech

| Model | Params | Task | Hardware | License | Best For |
|---|---:|---|---|---|---|
| [Whisper large-v3](https://huggingface.co/openai/whisper-large-v3) | 1.55B | Speech-to-Text | CPU / GPU / Apple Silicon (MLX, whisper.cpp) | Apache-2.0 | Multilingual transcription, translation |
| [Kokoro-82M](https://huggingface.co/hexgrad/Kokoro-82M) | 82M | Text-to-Speech | CPU (<2 GB) | Apache-2.0 | Lightweight, fast, real-time TTS (54 voices, 8 languages) |
| [F5-TTS](https://huggingface.co/SWivid/F5-TTS) | ~330M (DiT) | Text-to-Speech / Voice Cloning | ~4 GB VRAM | CC-BY-NC-4.0 (Research Only; commercial fine-tunes exist separately, e.g. Apache-2.0 OpenF5-TTS-Base) | Zero-shot voice cloning from a few seconds of reference audio |
| [MusicGen](https://huggingface.co/facebook/musicgen-large) | 300M–3.3B | Music Generation | ~8–16 GB VRAM (size-dependent) | Code: MIT / Weights: CC-BY-NC-4.0 (Research Only) | Text-to-music and melody-conditioned generation |
| [Qwen2.5-Omni-7B](https://huggingface.co/Qwen/Qwen2.5-Omni-7B) | 7B | Audio Understanding (+ text/image/video, real-time speech output) | ~16 GB (Q4) / ~20 GB (fp16) | Apache-2.0 | End-to-end audio/multimodal understanding + real-time speech generation |
| [pyannote speaker-diarization-3.1](https://huggingface.co/pyannote/speaker-diarization-3.1) | N/A (segmentation + embedding pipeline) | Speaker Recognition / Diarization | CPU/GPU | MIT | Who-spoke-when diarization for meeting/call transcripts |

- Trained on 1M hours of weakly labeled audio + 4M hours of pseudo-labeled audio, using 128 Mel-frequency bins (vs. 80 in large-v2) — a 10–20% error reduction over large-v2 across languages (Whisper large-v3). Smaller distilled/quantized Whisper variants (tiny, base, small, medium) trade accuracy for speed and run well on CPU.
- **Kokoro-82M**: despite its small size, reached #1 on the TTS Spaces Arena leaderboard at launch; runs in real-time or faster on budget CPU hardware, fully Apache-2.0.
- **F5-TTS**: flow-matching + diffusion-transformer voice cloning model; the original SWivid/F5-TTS weights are **CC-BY-NC-4.0** (non-commercial) — don't assume commercial use is fine without a separate license or an explicitly Apache-2.0 community fine-tune.
- **MusicGen**: Meta's text/melody-to-music model; code is MIT but the released **weights are CC-BY-NC-4.0**, restricting the official checkpoints to non-commercial research use.
- **Qwen2.5-Omni-7B**: a genuinely end-to-end omni-modal model (text+image+audio+video in, text+speech out), not audio-only — ranked #1 open-source on the MMAU audio understanding/reasoning leaderboard at release.
- **pyannote speaker-diarization-3.1**: the standard open pipeline for "who spoke when," MIT-licensed; the newer `speaker-diarization-community-1` pipeline is CC-BY-4.0 instead. Requires accepting gated-access terms on Hugging Face before download.
- Runs efficiently via `whisper.cpp` on CPU/Apple Silicon, or `faster-whisper`/CTranslate2 on GPU.

---

## 7. Retrieval

Text embedding and reranking models for semantic search and RAG.

| Model | Params | Context | VRAM | License | Best For |
|---|---:|---:|---:|---|---|
| [Qwen3-Embedding-0.6B](https://huggingface.co/Qwen/Qwen3-Embedding-0.6B) | 0.6B | 32K | ~2 GB | Apache-2.0 | Multilingual text embeddings, instruction-aware retrieval |
| [BGE-M3](https://huggingface.co/BAAI/bge-m3) | ~568M | 8K | ~2 GB | MIT | Multi-functionality retrieval (dense + sparse + multi-vector), multilingual RAG |
| [gte-Qwen2-7B-instruct](https://huggingface.co/Alibaba-NLP/gte-Qwen2-7B-instruct) | 7B | 32K | ~16 GB (fp16) / ~6 GB (Q4) | Apache-2.0 | Highest-quality open embeddings (top MTEB ranking), multilingual |
| [nomic-embed-text-v1.5](https://huggingface.co/nomic-ai/nomic-embed-text-v1.5) | 137M | 8192 | ~1 GB | Apache-2.0 | Lightweight embeddings with Matryoshka dimension truncation (768→64) |
| [mxbai-embed-large-v1](https://huggingface.co/mixedbread-ai/mxbai-embed-large-v1) | 335M | 512 | ~1.5 GB | Apache-2.0 | General-purpose semantic search / RAG on modest hardware |
| [jina-embeddings-v3](https://huggingface.co/jinaai/jina-embeddings-v3) | 570M | 8192 | ~2 GB | CC-BY-NC-4.0 (Research Only; commercial via Jina API/AWS/Azure) | Task-specific LoRA adapters (retrieval, clustering, classification) |
| [bge-reranker-v2-m3](https://huggingface.co/BAAI/bge-reranker-v2-m3) | 568M | 512 (per pair) | ~2 GB | Apache-2.0 | Reranking retrieved candidates, multilingual (EN/ZH strong, broad language support) |
| [jina-reranker-v2-base-multilingual](https://huggingface.co/jinaai/jina-reranker-v2-base-multilingual) | N/A | 1024 (per pair) | ~2 GB | CC-BY-NC-4.0 (Research Only; commercial via Jina API/AWS/Azure) | Multilingual cross-encoder reranking for RAG pipelines |

- **Qwen3-Embedding** family also ships 4B and 8B variants for higher retrieval quality at greater compute cost; all Apache-2.0.
- **BGE-M3** ("M3" = Multi-Linguality, Multi-Functionality, Multi-Granularity) supports 100+ languages and can produce dense, sparse (lexical), and ColBERT-style multi-vector embeddings from one model.
- **gte-Qwen2-7B-instruct**: built on the Apache-2.0 Qwen2-7B base by Alibaba-NLP; one of the strongest open embedding models on the MTEB leaderboard, at the cost of needing a 7B-class model just for embeddings.
- **nomic-embed-text-v1.5** and **mxbai-embed-large-v1**: both small, Apache-2.0, and CPU-friendly — the practical defaults when you want a fully permissive license without the compute cost of a 7B embedder. Nomic's Matryoshka training lets you truncate embeddings down to 64 dims for storage/speed trade-offs.
- **jina-embeddings-v3** and **jina-reranker-v2-base-multilingual**: both **CC-BY-NC-4.0** (non-commercial) when self-hosted from the Hugging Face weights — Jina AI's commercial terms require going through their paid API/cloud marketplace offerings instead. Don't assume these are commercially self-hostable for free.
- **bge-reranker-v2-m3**: pairs naturally with BGE-M3 or any embedding model above as a second-stage reranker; Apache-2.0 and lightweight enough to run alongside an embedding model on the same GPU.
- Most models here are CPU-runnable at small batch sizes and fit comfortably on any consumer GPU; the 7B-class embedder (gte-Qwen2-7B-instruct) is the exception.

---

## 8. Lightweight & Edge AI

Small language models built for CPU, mobile, and resource-constrained deployment.

| Model | Params | Context | VRAM | License | Best For |
|---|---:|---:|---:|---|---|
| [Phi-4-mini-instruct](https://huggingface.co/microsoft/Phi-4-mini-instruct) | 3.8B | 128K | ~4 GB (Q4) / ~8 GB (fp16) | MIT | Small language model, CPU-friendly, reasoning-dense tasks |
| [Gemma 3 4B](https://huggingface.co/google/gemma-3-4b-it) | 4B | 128K | ~4 GB (Q4) / ~8 GB (fp16) | Gemma Terms of Use (commercial allowed) | Small multimodal model (text + image), on-device |
| [Gemma 3 270M](https://huggingface.co/google/gemma-3-270m-it) | 270M | 32K | <1 GB (Q4) / ~1 GB (fp16) | Gemma Terms of Use (commercial allowed) | Ultra-lightweight text-only model, hyper-efficient edge/mobile deployment |
| [SmolLM2-1.7B](https://huggingface.co/HuggingFaceTB/SmolLM2-1.7B) | 1.7B (also 135M, 360M) | 8192 | ~1.5 GB (Q4) / ~4 GB (fp16) | Apache-2.0 | On-device general tasks, smallest sizes for CPU/browser (WebGPU) |
| [Qwen3-0.6B](https://huggingface.co/Qwen/Qwen3-0.6B) | 0.6B | 32K | ~1 GB (Q4) / ~2 GB (fp16) | Apache-2.0 | Smallest Qwen3 with thinking/non-thinking mode toggle, 100+ languages |
| [Llama 3.2 1B](https://huggingface.co/meta-llama/Llama-3.2-1B) | 1.23B | 128K (8K on quantized builds) | ~1 GB (Q4) / ~3 GB (fp16) | Llama 3.2 Community License (commercial allowed) | Meta's edge/mobile-optimized dense model |
| [TinyLlama-1.1B](https://huggingface.co/TinyLlama/TinyLlama-1.1B-Chat-v1.0) | 1.1B | 2048 | ~1 GB (Q4) / ~3 GB (fp16) | Apache-2.0 | Simplest fully-permissive baseline for Raspberry Pi / very constrained CPU |
| [MobileLLM-R1](https://huggingface.co/collections/facebook/mobilellm-r1-68c4597b104fac45f28f448e) | 140M–950M | 4K base / 32K post-trained | <1 GB (Q4) | FAIR NC (**non-commercial only**) | Best sub-1B reasoning benchmarks; research/personal use only |

- **Phi-4-mini**: text-only, trained on synthetic + filtered web data with a focus on reasoning density; MIT license is fully commercially usable without restriction.
- **Gemma 3 4B**: part of the Gemma 3 family (1B/4B/12B/27B); the 1B variant is text-only with a 32K context window, while 4B/12B/27B add image input and 128K context.
- **Gemma 3 270M**: the smallest Gemma 3 size, text-only, designed specifically for hyper-efficient edge deployment; still carries a 256K-token vocabulary for strong multilingual/rare-token handling despite its size.
- **SmolLM2**: Hugging Face's fully open small-model family (135M/360M/1.7B), Apache-2.0, commonly used for on-device and in-browser (WebGPU/transformers.js) demos.
- **Qwen3-0.6B**: shares the same thinking/non-thinking toggle and 100+ language support as larger Qwen3 models, just at edge scale; pairs naturally with Qwen3-Embedding-0.6B (see [Retrieval](#7-retrieval)) for a fully local, same-family RAG stack.
- **Llama 3.2 1B**: Meta's smallest Llama 3.2 size, purpose-built for edge/mobile; note the Llama Community License is custom (not Apache/MIT) though it does permit commercial use for most organizations.
- **TinyLlama-1.1B**: the oldest model in this table (pretrained on ~1T tokens of SlimPajama + StarCoderData) but still relevant as the simplest, most permissively licensed baseline for extremely constrained devices like Raspberry Pi — its native 2048-token context is far shorter than the newer models here.
- **MobileLLM-R1**: Meta's sub-1B reasoning-focused family, claimed 2–5x performance over other fully open sub-1B models on reasoning benchmarks — but licensed under **FAIR NC**, a non-commercial research license, unlike every other model in this table. Do not deploy it in a commercial product without a separate agreement from Meta.
- Everything above except MobileLLM-R1 and Gemma 3 270M's larger siblings runs comfortably on Apple Silicon (MLX/GGUF conversions), modern CPUs at Q4 quantization, and several (SmolLM2, Qwen3-0.6B) are small enough for in-browser WebGPU inference.

---

## 9. Document AI (OCR)

Small, locally-runnable vision-language models tuned for OCR, document parsing, and structured layout extraction (text/tables/formulas → Markdown or HTML).

| Model | Params | Context | VRAM | License | Best For |
|---|---:|---:|---:|---|---|
| [PaddleOCR-VL](https://huggingface.co/PaddlePaddle/PaddleOCR-VL) | 0.9B | N/A (page-level, not a general chat context window) | ~4 GB | Apache-2.0 | Lightweight, multi-language (100+ scripts) layout + text extraction |
| [OvisOCR2](https://huggingface.co/ATH-MaaS/OvisOCR2) | 0.8B | N/A (page-level) | ~4 GB | Apache-2.0 | SOTA document parsing (OmniDocBench v1.6 leader), LaTeX formula recognition |
| [GLM-OCR](https://huggingface.co/zai-org/GLM-OCR) | 0.9B | N/A (page-level) | ~4 GB | MIT (pipeline's PP-DocLayoutV3 component is Apache-2.0) | Easiest local deployment (Ollama, vLLM, SGLang), edge devices |
| [Qwen2.5-VL-3B-Instruct](https://huggingface.co/Qwen/Qwen2.5-VL-3B-Instruct) | 4.1B | 32K native (YaRN-extendable) | ~8 GB (Q4) / ~10 GB (fp16) | Apache-2.0 | General-purpose offline image-to-text and document structure extraction |
| [Nanonets-OCR-s](https://huggingface.co/nanonets/Nanonets-OCR-s) | 4B | 32K (inherited from base) | ~8 GB (Q4) / ~10 GB (fp16) | Unknown — fine-tune of Apache-2.0 Qwen2.5-VL-3B-Instruct, but Nanonets has not published an explicit license for the fine-tuned weights ([see HF discussion](https://huggingface.co/nanonets/Nanonets-OCR-s/discussions/2)) | Scanned documents, handwriting, and tables → clean Markdown |

- **PaddleOCR-VL** and **OvisOCR2** are both sub-1B, purpose-built document parsers (not general chat models) — PaddleOCR-VL pairs a NaViT-style dynamic-resolution encoder with the 0.3B ERNIE-4.5 language model; OvisOCR2 is a post-trained Qwen3.5-0.8B. Both top OmniDocBench v1.6 among sub-1B models as of their release.
- **GLM-OCR**: Z.ai's 0.9B model, MIT-licensed, explicitly designed for consumer-laptop/edge deployment; its full pipeline optionally uses PP-DocLayoutV3 (Apache-2.0) for layout analysis.
- **Qwen2.5-VL-3B-Instruct**: a general vision-language model (not OCR-specialized) that's widely used for offline document/image-to-text via Ollama or LM Studio; Apache-2.0, unlike some larger Qwen2.5-VL sizes.
- **Nanonets-OCR-s**: fine-tuned from Qwen2.5-VL-3B-Instruct specifically for markdown conversion of scanned docs/handwriting/tables. Its base model is Apache-2.0, but Nanonets itself has not clearly republished a license for the fine-tune — treat commercial use as **unverified** until Nanonets clarifies (see the linked HF discussion) rather than assuming it inherits Apache-2.0.
- Context length is listed as `N/A` for the three dedicated OCR parsers above because they operate on single-page images with a fixed output budget rather than exposing a general long-context chat window; check each repo for exact page-resolution and output-token limits.
- **PaddleOCR** (the classical, non-VLM pipeline: PP-OCRv6) is a separate, much smaller (1.5M–34.5M param) detection+recognition stack from the same team, also Apache-2.0 — worth considering over the VLM-based models above when you need maximum speed on CPU/edge rather than markdown-quality structure extraction.

---

## How to Choose a Model

1. **Start from the task**, not the model — pick the category/subcategory that matches what you're building (e.g. "Coding Agents", not just "Coding").
2. **Check the license** against your use case — `Commercial Restricted` and `Research Only` models (e.g. FLUX.1 [dev]) cannot be used in a commercial product without a separate agreement.
3. **Match hardware before quality** — a model you can't run locally or afford to serve isn't the "best" model for you. Use the [hardware table](#hardware-based-recommendations) as a first filter.
4. **Prefer dense models for simplicity, MoE for throughput** — MoE models (Llama 4, Qwen3-Coder-480B, DeepSeek-V3.1/R1) need more total VRAM/disk but only activate a fraction of parameters per token.
5. **Check context length against your actual input size** — advertised maximums (e.g. Llama 4 Scout's 10M) often require specialized serving setups; treat the "native" context length as the reliable baseline.

---

## Model Selection Criteria

1. **Relevance** — does it solve a real and useful problem?
2. **Accessibility** — can developers actually download and use it?
3. **Documentation** — sufficient docs provided?
4. **License** — is the licensing clear?
5. **Adoption** — meaningful community/ecosystem support?
6. **Performance** — useful benchmarks or demonstrated capabilities?
7. **Maintenance** — prefer actively maintained projects when alternatives are comparable.

No minimum star count — a smaller model can belong here if it's useful, well-documented, and clearly licensed.

---

## Contributing

Contributions are welcome — new models, corrections to outdated specs, new categories. Before adding a model: verify the official source, license, and specs (never invent numbers). Add your entry directly to the matching category section above, keeping the existing table format. See [CONTRIBUTING.md](CONTRIBUTING.md) for the full checklist and PR template.

## License

The content and structure of this directory are licensed under [MIT](LICENSE). Each listed model retains its own license — always check the linked official source before using a model.
