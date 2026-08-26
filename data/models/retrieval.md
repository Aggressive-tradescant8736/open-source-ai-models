# Retrieval

Text embedding and reranking models for semantic search and RAG.

| Model | Params | Context | VRAM | License | Best For |
|---|---:|---:|---:|---|---|
| [Qwen3-Embedding-0.6B](https://huggingface.co/Qwen/Qwen3-Embedding-0.6B) | 0.6B | 32K | ~2 GB | Apache-2.0 | Multilingual text embeddings, instruction-aware retrieval |
| [BGE-M3](https://huggingface.co/BAAI/bge-m3) | ~568M | 8K | ~2 GB | MIT | Multi-functionality retrieval (dense + sparse + multi-vector), multilingual RAG |

## Notes

- **Qwen3-Embedding** family also ships 4B and 8B variants for higher retrieval quality at greater compute cost; all are Apache-2.0.
- **BGE-M3** ("M3" = Multi-Linguality, Multi-Functionality, Multi-Granularity) supports over 100 languages and can produce dense, sparse (lexical), and ColBERT-style multi-vector embeddings from a single model.
- Both models are CPU-runnable at small batch sizes and comfortably fit on any consumer GPU.

See also: [Multimodal](multimodal.md) for cross-modal embedding needs.
