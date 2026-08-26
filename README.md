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

**🏆 Best Overall** — [DeepSeek-V3.1](#1-general-ai): 671B/37B-active MoE, hybrid think/non-think mode, 128K context, commercially usable license.

**💻 Best Coding Models** — [Qwen3-Coder-480B-A35B-Instruct](#2-coding) for server-scale agentic coding; [Qwen3-Coder-30B-A3B-Instruct](#2-coding) for local/single-GPU use.

**🧠 Best Reasoning Models** — [DeepSeek-R1](#1-general-ai) (MIT, frontier, distillation source), [Qwen3-235B-A22B-Thinking-2507](#1-general-ai) (262K context), [QwQ-32B](#1-general-ai) (single-GPU, ~24 GB Q4).

**👁️ Best Vision-Language Models** — [Gemma 3 27B](#3-multimodal): multilingual text+image input, 128K context, permissive commercial license.

**✂️ Best Background Removal Models** — [BiRefNet](#5-image-matting--background-removal) (MIT, highest quality/resolution) for general use; [U2-Net](#5-image-matting--background-removal) family (Apache-2.0) for subject-specific variants (Human, Cloth, Anime via IS-Net); [Silueta](#5-image-matting--background-removal) (~43 MB) when file size matters more than accuracy.

**🎨 Best Image Generation Models** — [FLUX.1 \[schnell\]](#4-image-generation) for commercial use (Apache-2.0); [FLUX.1 \[dev\]](#4-image-generation) for max quality, non-commercial only.

**🎙️ Best Speech-to-Text Models** — [Whisper large-v3](#6-audio--speech): Apache-2.0, multilingual, runs on CPU via `whisper.cpp`.

**📄 Best OCR Models** — [PaddleOCR-VL](#9-document-ai-ocr) (0.9B, Apache-2.0) and [OvisOCR2](#9-document-ai-ocr) (0.8B, Apache-2.0) for SOTA document parsing at sub-1B size; [GLM-OCR](#9-document-ai-ocr) (0.9B, MIT) for the easiest local/Ollama deployment.

**🔍 Best Retrieval / Embedding Models** — [Qwen3-Embedding-0.6B](#7-retrieval) for multilingual instruction-aware retrieval; [BGE-M3](#7-retrieval) for dense+sparse+multi-vector RAG.

**🪶 Best Small Models** — [Phi-4-mini-instruct](#8-lightweight--edge-ai) (3.8B, MIT) for text-only edge; [Gemma 3 4B](#8-lightweight--edge-ai) for on-device multimodal.

**🔒 Best for Local / Private AI** — [Qwen3-32B](#1-general-ai) and [Qwen3-Coder-30B-A3B-Instruct](#2-coding): both Apache-2.0, run at ~24 GB VRAM quantized.

---

## Hardware-Based Recommendations

| Tier | Recommended models |
|---|---|
| 🟢 CPU | Whisper large-v3 (via whisper.cpp), BGE-M3, BiRefNet, PaddleOCR-VL, OvisOCR2, GLM-OCR |
| 🟢 8 GB VRAM | Qwen3-Embedding-0.6B, Phi-4-mini-instruct, Gemma 3 4B, Qwen2.5-VL-3B-Instruct, Nanonets-OCR-s |
| 🟢 24 GB VRAM | Qwen3-32B (Q4), QwQ-32B (Q4), Qwen3-Coder-30B-A3B-Instruct (Q4), Gemma 3 27B (Q4), FLUX.1 [dev] (quantized) |
| 🟢 48 GB+ VRAM | DeepSeek-V3.1, DeepSeek-R1, Qwen3-235B-A22B-Thinking-2507, Llama 4 Scout, Qwen3-Coder-480B-A35B-Instruct *(multi-GPU or aggressive quantization at this tier)* |
| 🍎 Apple Silicon | Whisper large-v3 (MLX/whisper.cpp), Qwen3-32B (MLX/GGUF), Phi-4-mini-instruct (MLX/GGUF) |

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

- **Llama 4 Scout**: MoE with 16 experts; the 10M-token context is Meta's advertised maximum and needs specialized long-context serving. Larger sibling Llama 4 Maverick (400B total / 17B active, 1M context) exists for higher-quality workloads.
- **Qwen3-32B**: part of the Qwen3 dense family (0.6B–32B); larger MoE variants (30B-A3B, 235B-A22B) trade dense simplicity for throughput at similar active-parameter cost.
- **DeepSeek-V3.1**: code released under MIT; model weights follow DeepSeek's own model license. 128K is the documented baseline context; some providers expose up to 163,840 tokens.

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

- Both variants share the Qwen3-Coder architecture, tuned specifically for agentic coding workflows (tool use, long-context repo understanding) rather than general chat.
- The 480B model targets server/multi-GPU deployment; 30B-A3B is the practical choice for local or single-GPU use given its much lower active-parameter footprint.
- For general-purpose models that also perform reasonably at code (e.g. DeepSeek-V3.1), see [General AI](#1-general-ai).

---

## 3. Multimodal

Vision-language and other cross-modal models.

| Model | Params | Context | VRAM | License | Best For |
|---|---:|---:|---:|---|---|
| [Gemma 3 27B](https://huggingface.co/google/gemma-3-27b-it) | 27B | 128K | ~24 GB (Q4) / ~54 GB (fp16) | Gemma Terms of Use (commercial allowed) | Vision-language, multilingual multimodal reasoning |

- Gemma 3's 4B, 12B, and 27B variants all accept text + image input with text output; the 1B variant is text-only (see [Lightweight & Edge AI](#8-lightweight--edge-ai)).
- Google's Gemma license is a custom permissive license, not Apache/MIT — classify as **Commercial Allowed**, not plain "Open Source."
- Llama 4 (see [General AI](#1-general-ai)) is also multimodal (text + image in, text out) and can be cross-referenced for larger-scale vision-language needs.

---

## 4. Image Generation

| Model | Params | Task | VRAM | License | Best For |
|---|---:|---|---:|---|---|
| [FLUX.1 \[schnell\]](https://huggingface.co/black-forest-labs/FLUX.1-schnell) | 12B | Text-to-Image | ~16 GB (fp16) / ~8 GB (quantized) | Apache-2.0 | Fast text-to-image generation, commercial use |
| [FLUX.1 \[dev\]](https://huggingface.co/black-forest-labs/FLUX.1-dev) | 12B | Text-to-Image | ~24 GB (fp16) / ~12 GB (quantized) | FLUX.1 [dev] Non-Commercial License | Highest-quality open-weight text-to-image, research/personal use |

- Both share the same 12B-parameter rectified-flow transformer from Black Forest Labs. **schnell** is distilled for few-step (1–4 step) fast inference and is Apache-2.0 (commercial use allowed); **dev** is the higher-fidelity guidance-distilled variant restricted to non-commercial use.
- Black Forest Labs also offers **FLUX.1 Pro/Flex** (proprietary, API-only) and **FLUX.1 Kontext [dev]** (12B, image editing, same non-commercial license as [dev]).
- Do not describe FLUX.1 [dev] as "open source" — it is **Open Weight** with commercial restrictions.

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

- Trained on 1M hours of weakly labeled audio + 4M hours of pseudo-labeled audio, using 128 Mel-frequency bins (vs. 80 in large-v2) — a 10–20% error reduction over large-v2 across languages.
- Smaller distilled/quantized variants (tiny, base, small, medium) trade accuracy for speed and run well on CPU.
- Runs efficiently via `whisper.cpp` on CPU/Apple Silicon, or `faster-whisper`/CTranslate2 on GPU.
- Text-to-Speech, Voice Cloning, and Music Generation entries are welcome — see [Contributing](#contributing).

---

## 7. Retrieval

Text embedding and reranking models for semantic search and RAG.

| Model | Params | Context | VRAM | License | Best For |
|---|---:|---:|---:|---|---|
| [Qwen3-Embedding-0.6B](https://huggingface.co/Qwen/Qwen3-Embedding-0.6B) | 0.6B | 32K | ~2 GB | Apache-2.0 | Multilingual text embeddings, instruction-aware retrieval |
| [BGE-M3](https://huggingface.co/BAAI/bge-m3) | ~568M | 8K | ~2 GB | MIT | Multi-functionality retrieval (dense + sparse + multi-vector), multilingual RAG |

- **Qwen3-Embedding** family also ships 4B and 8B variants for higher retrieval quality at greater compute cost; all Apache-2.0.
- **BGE-M3** ("M3" = Multi-Linguality, Multi-Functionality, Multi-Granularity) supports 100+ languages and can produce dense, sparse (lexical), and ColBERT-style multi-vector embeddings from one model.
- Both are CPU-runnable at small batch sizes and fit comfortably on any consumer GPU.

---

## 8. Lightweight & Edge AI

Small language models built for CPU, mobile, and resource-constrained deployment.

| Model | Params | Context | VRAM | License | Best For |
|---|---:|---:|---:|---|---|
| [Phi-4-mini-instruct](https://huggingface.co/microsoft/Phi-4-mini-instruct) | 3.8B | 128K | ~4 GB (Q4) / ~8 GB (fp16) | MIT | Small language model, CPU-friendly, reasoning-dense tasks |
| [Gemma 3 4B](https://huggingface.co/google/gemma-3-4b-it) | 4B | 128K | ~4 GB (Q4) / ~8 GB (fp16) | Gemma Terms of Use (commercial allowed) | Small multimodal model (text + image), on-device |

- **Phi-4-mini**: text-only, trained on synthetic + filtered web data with a focus on reasoning density; MIT license is fully commercially usable without restriction.
- **Gemma 3 4B**: part of the Gemma 3 family (1B/4B/12B/27B); the 1B variant is text-only with a 32K context window, while 4B/12B/27B add image input and 128K context.
- Both run comfortably on Apple Silicon (MLX/GGUF conversions) and modern CPUs at Q4 quantization.

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
