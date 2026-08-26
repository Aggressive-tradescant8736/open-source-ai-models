# Open Source AI Models

> A curated directory of open-source and open-weight AI models for developers, researchers, and AI builders.

Find the right AI model for coding, OCR, computer vision, image generation, speech, reasoning, RAG, agents, and more — with the parameters, hardware requirements, and license you need to actually decide, not just a link.

This is a **directory**, not an *Awesome List*: every entry lists params, VRAM, context length, license, and best-use-case so you can compare models instead of just discovering them.

---

## Categories

- [General AI](data/models/general-ai.md) — General LLM, Reasoning, Mathematics, Multilingual, Instruction Following
- [Coding](data/models/coding.md) — Code Generation, Code Completion, Code Review, Coding Agents
- Computer Vision — Image Classification, Object Detection, Segmentation, Pose Estimation, Face Analysis *(seed pending)*
- Document AI — OCR, Document Understanding, Table Recognition, Layout Analysis *(seed pending)*
- [Image Generation](data/models/image-generation.md) — Text-to-Image, Image Editing, Inpainting, Super Resolution
- Video — Text-to-Video, Video Understanding, Video Editing *(seed pending)*
- [Audio & Speech](data/models/audio-speech.md) — Speech-to-Text, Text-to-Speech, Voice Cloning, Music Generation
- [Multimodal](data/models/multimodal.md) — Vision-Language, Audio-Language, Video-Language
- [Retrieval](data/models/retrieval.md) — Text Embeddings, Reranking, Semantic Search, RAG
- Language — Translation, Summarization, Text Classification, Sentiment Analysis *(seed pending)*
- Agents — Computer Use, GUI Agents, Browser Agents, Robotics *(seed pending)*
- [Lightweight & Edge AI](data/models/lightweight-edge-ai.md) — Small Language Models, CPU-Friendly, Mobile, WebGPU

See [`data/categories/categories.md`](data/categories/categories.md) for the full taxonomy, and [Image Matting & Background Removal](data/models/image-matting-background-removal.md) for the background-removal specialization tree (General / Human / Clothing / Animal / Product / Anime).

*Categories marked "seed pending" are defined in the taxonomy but don't have a verified model entry yet — see [Contributing](#contributing) if you'd like to add one.*

---

## Featured

### 🏆 Best Overall
[DeepSeek-V3.1](data/models/general-ai.md) — 671B/37B-active MoE with a hybrid think/non-think mode, 128K context, commercially usable license. Best when you can run multi-GPU inference and want frontier-level reasoning + general capability in one model.

### 💻 Best Coding Models
[Qwen3-Coder-480B-A35B-Instruct](data/models/coding.md) for server-scale agentic coding; [Qwen3-Coder-30B-A3B-Instruct](data/models/coding.md) for local/single-GPU use — both Apache-2.0 with 256K native context built specifically for coding agents.

### 🧠 Best Reasoning Models
[DeepSeek-V3.1](data/models/general-ai.md) — explicit hybrid reasoning mode with strong benchmark results at 128K context.

### 👁️ Best Vision-Language Models
[Gemma 3 27B](data/models/multimodal.md) — multilingual text+image input, 128K context, permissive commercial license.

### ✂️ Best Background Removal Models
[BiRefNet](data/models/image-matting-background-removal.md) — MIT-licensed, high-resolution dichotomous image segmentation, the current standard backbone behind most open background-removal tooling.

### 🎨 Best Image Generation Models
[FLUX.1 \[schnell\]](data/models/image-generation.md) for commercial use (Apache-2.0, fast few-step generation); [FLUX.1 \[dev\]](data/models/image-generation.md) for maximum quality if your use case is non-commercial.

### 🎙️ Best Speech-to-Text Models
[Whisper large-v3](data/models/audio-speech.md) — Apache-2.0, multilingual transcription and translation, runs on CPU via `whisper.cpp`.

### 🔍 Best Retrieval / Embedding Models
[Qwen3-Embedding-0.6B](data/models/retrieval.md) for multilingual instruction-aware retrieval; [BGE-M3](data/models/retrieval.md) for combined dense+sparse+multi-vector retrieval in RAG pipelines.

### 🪶 Best Small Models
[Phi-4-mini-instruct](data/models/lightweight-edge-ai.md) (3.8B, MIT, 128K context) for text-only edge deployment; [Gemma 3 4B](data/models/lightweight-edge-ai.md) if you need on-device multimodal (text+image).

### 🔒 Best Models for Local / Private AI
[Qwen3-32B](data/models/general-ai.md) (Apache-2.0, runs at ~24 GB VRAM quantized) and [Qwen3-Coder-30B-A3B-Instruct](data/models/coding.md) for a fully local, commercially-clean stack.

---

## Hardware-Based Recommendations

| Tier | Recommended models |
|---|---|
| 🟢 CPU | [Whisper large-v3](data/models/audio-speech.md) (via whisper.cpp), [BGE-M3](data/models/retrieval.md), [BiRefNet](data/models/image-matting-background-removal.md) |
| 🟢 8 GB VRAM | [Qwen3-Embedding-0.6B](data/models/retrieval.md), [Phi-4-mini-instruct](data/models/lightweight-edge-ai.md), [Gemma 3 4B](data/models/lightweight-edge-ai.md) |
| 🟢 24 GB VRAM | [Qwen3-32B](data/models/general-ai.md) (Q4), [Qwen3-Coder-30B-A3B-Instruct](data/models/coding.md) (Q4), [Gemma 3 27B](data/models/multimodal.md) (Q4), [FLUX.1 \[dev\]](data/models/image-generation.md) (quantized) |
| 🟢 48 GB+ VRAM | [DeepSeek-V3.1](data/models/general-ai.md), [Llama 4 Scout](data/models/general-ai.md), [Qwen3-Coder-480B-A35B-Instruct](data/models/coding.md) (all require multi-GPU or aggressive quantization at this tier) |
| 🍎 Apple Silicon | [Whisper large-v3](data/models/audio-speech.md) (MLX/whisper.cpp), [Qwen3-32B](data/models/general-ai.md) (MLX/GGUF), [Phi-4-mini-instruct](data/models/lightweight-edge-ai.md) (MLX/GGUF) |

VRAM figures are approximate, quantization-dependent estimates for guidance only — see each model's page for sourcing and always verify against the official model card before provisioning hardware.

---

## How to Choose a Model

1. **Start from the task**, not the model — pick the category/subcategory that matches what you're building (e.g. "Coding Agents", not just "Coding").
2. **Check the license** against your use case — `Commercial Restricted` and `Research Only` models (e.g. FLUX.1 [dev]) cannot be used in a commercial product without a separate agreement.
3. **Match hardware before quality** — a model you can't run locally or afford to serve isn't the "best" model for you. Use the [hardware table](#hardware-based-recommendations) above as a first filter.
4. **Prefer dense models for simplicity, MoE for throughput** — MoE models (Llama 4, Qwen3-Coder-480B, DeepSeek-V3.1) need more total VRAM/disk but only activate a fraction of parameters per token, which can mean faster inference than a dense model of equivalent active size.
5. **Check context length against your actual input size** — advertised maximums (e.g. Llama 4 Scout's 10M) often require specialized serving setups to realize in practice; treat the "native" context length as the reliable baseline.

---

## Contributing

Contributions are welcome — new models, corrections to outdated specs, and new categories.

Before adding a model: verify the official source, license, and specs (never invent numbers). See [CONTRIBUTING.md](CONTRIBUTING.md) for the full checklist, entry format, and PR template. Model data lives in [`data/models/`](data/models/); the category taxonomy is in [`data/categories/categories.md`](data/categories/categories.md).

## License

The content and structure of this directory are licensed under [MIT](LICENSE). Each listed model retains its own license — always check the linked official source before using a model.
