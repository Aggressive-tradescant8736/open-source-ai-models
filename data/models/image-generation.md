# Image Generation

| Model | Params | Task | Hardware | License | Best For |
|---|---:|---|---|---|---|
| [FLUX.1 \[schnell\]](https://huggingface.co/black-forest-labs/FLUX.1-schnell) | 12B | Text-to-Image | ~16 GB VRAM (fp16) / ~8 GB (quantized) | Apache-2.0 | Fast text-to-image generation, commercial use |
| [FLUX.1 \[dev\]](https://huggingface.co/black-forest-labs/FLUX.1-dev) | 12B | Text-to-Image | ~24 GB VRAM (fp16) / ~12 GB (quantized) | FLUX.1 [dev] Non-Commercial License | Highest-quality open-weight text-to-image, research/personal use |

## Notes

- Both models share the same 12B-parameter rectified-flow transformer architecture from Black Forest Labs; **schnell** is distilled for few-step (1–4 step) fast inference and is fully Apache-2.0 (commercial use allowed), while **dev** is the higher-fidelity guidance-distilled variant restricted to non-commercial use.
- Black Forest Labs also offers **FLUX.1 Pro/Flex** (proprietary, API-only) and **FLUX.1 Kontext [dev]** (12B, image editing) — Kontext [dev] carries the same non-commercial license as [dev].
- Do not describe FLUX.1 [dev] as "open source" — it is **Open Weight** with commercial restrictions.

See also: [Image Matting & Background Removal](image-matting-background-removal.md) for editing/matting-adjacent tasks.
