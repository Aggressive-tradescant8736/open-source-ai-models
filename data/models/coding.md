# Coding

Code generation, completion, and coding-agent models.

| Model | Params | Context | VRAM | License | Best For |
|---|---:|---:|---:|---|---|
| [Qwen3-Coder-480B-A35B-Instruct](https://huggingface.co/Qwen/Qwen3-Coder-480B-A35B-Instruct) | 480B total / 35B active (MoE) | 256K native / 1M (YaRN) | Multi-GPU (>240 GB, quantized) | Apache-2.0 | Coding agents, repository-scale understanding |
| [Qwen3-Coder-30B-A3B-Instruct](https://huggingface.co/Qwen/Qwen3-Coder-30B-A3B-Instruct) | 30B total / 3B active (MoE) | 256K native / 1M (YaRN) | ~24 GB (Q4) | Apache-2.0 | Local coding agent, single-GPU / high-end consumer setups |

## Notes

- Both variants share the Qwen3-Coder architecture and are tuned specifically for agentic coding workflows (tool use, long-context repo understanding) rather than general chat.
- The 480B model is intended for server/multi-GPU deployment; the 30B-A3B variant is the practical choice for local or single-GPU use given its much lower active-parameter footprint.
- For lighter-weight coding on constrained hardware, see [Lightweight & Edge AI](lightweight-edge-ai.md).

See also: [General AI](general-ai.md) for general-purpose models that also perform reasonably at code tasks (e.g. DeepSeek-V3.1).
