# General AI

General-purpose LLMs, reasoning, and instruction-following models.

| Model | Params | Context | VRAM | License | Best For |
|---|---:|---:|---:|---|---|
| [Llama 4 Scout](https://www.llama.com/docs/model-cards-and-prompt-formats/llama4/) | 109B total / 17B active (MoE) | 10M tokens | ~66 GB (int4, active experts) / multi-GPU for full weights | Llama 4 Community License (commercial allowed under 700M MAU) | General LLM, long-context, multimodal (text+image in) |
| [Qwen3-32B](https://huggingface.co/Qwen/Qwen3-32B) | 32B (dense) | 32K native / 131K (YaRN) | ~24 GB (Q4) / ~64 GB (fp16) | Apache-2.0 | General LLM, instruction following, reasoning toggle |
| [DeepSeek-V3.1](https://huggingface.co/deepseek-ai/DeepSeek-V3.1) | 671B total / 37B active (MoE) | 128K | Multi-GPU (>400 GB fp8) | DeepSeek Model License (commercial use allowed) | Reasoning, general LLM, hybrid think/non-think mode |

## Notes

- **Llama 4 Scout**: MoE architecture with 16 experts; the 10M-token context figure is Meta's advertised maximum and requires specialized long-context serving infrastructure. Larger sibling Llama 4 Maverick (400B total / 17B active, 1M context) exists for higher-quality workloads.
- **Qwen3-32B**: Part of the Qwen3 dense family (0.6B–32B); larger Qwen3 MoE variants (30B-A3B, 235B-A22B) trade dense simplicity for higher throughput at similar active-parameter cost.
- **DeepSeek-V3.1**: Code released under MIT; model weights follow DeepSeek's own model license. Context length is reported as 128K by the model card, though some inference providers expose up to 163,840 tokens — treat 128K as the documented baseline.

See also: [Coding](coding.md), [Lightweight & Edge AI](lightweight-edge-ai.md) for smaller general-purpose models.
