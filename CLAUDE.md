# Open Source AI Models

## Project Overview

**Repository:** `open-source-ai-models`

Build and maintain a high-quality, community-friendly directory of **open-source and open-weight AI models**, organized by category, use case, model size, hardware requirements, modality, and license.

The primary goal is to make it easy for developers, researchers, and AI enthusiasts to answer:

> **"Which AI model should I use for this task?"**

This repository should be more useful than a simple collection of model links. Every entry should provide enough structured information for users to quickly compare models and choose the right one.

---

## Core Principles

1. **Useful over exhaustive**

   * Prioritize useful, relevant, and actively maintained models.
   * Do not add models simply to increase the number of entries.

2. **Accuracy first**

   * Never invent model specifications.
   * Verify model information from official sources whenever possible.
   * Clearly mark uncertain or unavailable information as `Unknown` or `N/A`.

3. **Developer focused**

   * Prioritize information developers actually need:

     * Parameters
     * Model size
     * VRAM requirements
     * Context length
     * Quantization
     * License
     * Supported modalities
     * Hardware compatibility
     * Main use case

4. **Easy to scan**

   * Use consistent tables.
   * Keep descriptions concise.
   * Avoid unnecessary marketing language.

5. **Open-source transparency**

   * Clearly distinguish between:

     * Open Source
     * Open Weight
     * Research-only
     * Restricted licenses
     * Commercially usable models

6. **Hardware awareness**

   * Hardware requirements are a major part of the project.
   * Whenever possible, indicate whether a model can run on:

     * CPU
     * Apple Silicon
     * NVIDIA GPU
     * AMD GPU
     * Mobile
     * WebGPU
     * Edge devices

---

# Repository Structure

```text
open-source-ai-models/
├── README.md
├── CLAUDE.md
├── CONTRIBUTING.md
├── LICENSE
├── CODE_OF_CONDUCT.md
├── SECURITY.md
└── .github/
    ├── ISSUE_TEMPLATE/
    └── pull_request_template.md
```

Single-file design, intentionally: `README.md` is the entire directory — every category is a numbered section (`## 1. General AI`, `## 2. Coding`, ...) with its model tables inline, plus a Contents TOC, Featured picks, and hardware-tier recommendations at the top. There is no separate `data/` folder — keeping everything in one file mirrors the readability of projects like `codecrafters-io/build-your-own-x` and `alvinreal/awesome-opensource-ai`, while keeping the structured comparison tables (params/VRAM/context/license) that make this a *directory* rather than a plain link list.

---

# Model Categories

## General AI
General LLM, Reasoning, Mathematics, Multilingual, Instruction Following

## Coding
Code Generation, Code Completion, Code Review, Code Explanation, Coding Agents

## Computer Vision
Image Classification, Object Detection, Image Segmentation, Image Matting, Background Removal, Image Understanding, Image Embeddings, Pose Estimation, Face Analysis

## Document AI
OCR, Document Understanding, Document Parsing, Table Recognition, Handwriting Recognition, Layout Analysis, PDF Understanding

## Image Generation
Text-to-Image, Image-to-Image, Image Editing, Inpainting, Outpainting, Super Resolution, Background Removal, Image Restoration

## Video
Text-to-Video, Image-to-Video, Video Generation, Video Understanding, Video Editing, Video Restoration

## Audio & Speech
Speech-to-Text, Text-to-Speech, Voice Cloning, Audio Understanding, Music Generation, Audio Generation, Speaker Recognition

## Multimodal
Vision-Language, Audio-Language, Video-Language, Multimodal Reasoning

## Retrieval
Text Embeddings, Multimodal Embeddings, Reranking, Semantic Search, RAG

## Language
Translation, Summarization, Text Classification, Sentiment Analysis, Language Detection, Information Extraction

## Agents
Computer Use, GUI Agents, Browser Agents, Coding Agents, Robotics

## Lightweight & Edge AI
Small Language Models, CPU-Friendly Models, Mobile AI, WebGPU, Raspberry Pi, Edge Devices, Embedded AI

---

# Image Matting & Background Removal

This category is particularly important.

```text
Image Matting & Background Removal
├── General
├── Human / Portrait
├── Clothing
├── Animal
├── Product
└── Anime / Illustration
```

| Model        | Category           | Specialization       |
| ------------ | ------------------ | --------------------- |
| U2-Net       | Background Removal | General              |
| BiRefNet     | Background Removal | General              |
| U2-Net Human | Background Removal | Human                |
| U2-Net Cloth | Background Removal | Clothing             |
| IS-Net       | Background Removal | Anime / Illustration |

Do not assume that every segmentation model is a background-removal model. Classify models according to their actual intended use.

---

# Model Entry Format

Preferred table structure for LLMs:

```markdown
| Model | Params | Size | Context | VRAM | License | Best For |
|---|---:|---:|---:|---:|---|---|
| Model Name | 7B | 4.5 GB | 128K | ~8 GB | Apache-2.0 | Coding |
```

For vision and non-LLM models, adapt the columns:

```markdown
| Model | Size | Task | Hardware | License | Best For |
|---|---:|---|---|---|---|
| BiRefNet | ~200 MB | Matting | CPU/GPU | MIT | Background Removal |
```

---

# Required Model Metadata

When available, collect: model name, organization/author, official repository, Hugging Face page, model family, category, subcategory, parameters, model file size, architecture, context length, input modality, output modality, VRAM requirement, CPU/GPU/Apple Silicon/mobile support, quantization availability, license, commercial usage, training information, release date, latest update, best use cases, limitations.

Never fabricate missing values — use `N/A` when genuinely unavailable.

---

# Hardware Classification

```text
🟢 CPU
🟢 4 GB VRAM
🟢 8 GB VRAM
🟢 12 GB VRAM
🟢 16 GB VRAM
🟢 24 GB VRAM
🟢 48 GB+ VRAM
🟢 Apple Silicon
🟢 Mobile
🟢 Edge
```

Use approximate requirements only when supported by documentation or reliable benchmarks. Do not present estimates as official requirements.

---

# Model Size Classification

```text
Tiny       < 1B
Small      1B–3B
Medium     3B–8B
Large      8B–30B
XL         30B–100B
Huge       100B+
```

Guidelines, not strict scientific classifications. For non-LLM models, do not force parameter-size classifications when they are not meaningful.

---

# License Classification

```text
Open Source
Open Weight
Research Only
Commercial Allowed
Commercial Restricted
Unknown
```

Provide the exact license when possible (Apache-2.0, MIT, BSD-3-Clause, GPL-3.0, Llama License, Gemma Terms, Qwen License, Custom License). Do not call a model "open source" solely because its weights are downloadable. When ambiguous, use **Open Weight** or **Unknown** rather than assuming.

---

# Model Selection Criteria

When deciding whether a model belongs in the directory:

1. **Relevance** — does it solve a real and useful problem?
2. **Accessibility** — can developers actually download and use it?
3. **Documentation** — sufficient docs provided?
4. **License** — is the licensing clear?
5. **Adoption** — meaningful community/ecosystem support?
6. **Performance** — useful benchmarks or demonstrated capabilities?
7. **Maintenance** — prefer actively maintained projects when alternatives are comparable.

---

# Quality Standards

Do not: invent benchmarks, invent VRAM requirements, invent licenses, call closed-source models open source, add unrelated AI tools as models, add duplicate models, use excessive promotional language, copy descriptions verbatim from model pages, add dead or suspicious download links.

Do: keep information factual, keep entries concise, prefer official sources, explain useful differences between similar models, highlight practical hardware requirements, maintain consistent formatting.

---

# Development Philosophy

Keep the project simple, fast, readable, community-driven, vendor-neutral, factual, and developer-friendly.

The most important metric is **usefulness**, not the number of models listed. When in doubt, prefer a smaller list of high-quality models over a huge list of poorly documented entries.

> **A practical "find the right AI model" directory rather than just another Awesome List.**
