# Lightweight & Edge AI

Small language models built for CPU, mobile, and resource-constrained deployment.

| Model | Params | Context | VRAM | License | Best For |
|---|---:|---:|---:|---|---|
| [Phi-4-mini-instruct](https://huggingface.co/microsoft/Phi-4-mini-instruct) | 3.8B | 128K | ~4 GB (Q4) / ~8 GB (fp16) | MIT | Small language model, CPU-friendly, reasoning-dense tasks |
| [Gemma 3 4B](https://huggingface.co/google/gemma-3-4b-it) | 4B | 128K | ~4 GB (Q4) / ~8 GB (fp16) | Gemma Terms of Use (commercial allowed) | Small multimodal model (text + image), on-device |

## Notes

- **Phi-4-mini**: text-only, trained on synthetic + filtered web data with a focus on reasoning density; MIT license makes it fully commercially usable without restriction.
- **Gemma 3 4B**: part of the Gemma 3 family (1B/4B/12B/27B); the 1B variant is text-only with a 32K context window, while 4B/12B/27B add image input and the 128K context window. Google's Gemma license is permissive for most commercial use but is a custom license, not Apache/MIT.
- Both models run comfortably on Apple Silicon (via MLX/GGUF conversions) and modern CPUs at Q4 quantization.

See also: [General AI](general-ai.md) for larger models in the same families (Qwen3, Llama 4).
