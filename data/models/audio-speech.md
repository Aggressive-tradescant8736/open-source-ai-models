# Audio & Speech

| Model | Params | Task | Hardware | License | Best For |
|---|---:|---|---|---|---|
| [Whisper large-v3](https://huggingface.co/openai/whisper-large-v3) | 1.55B | Speech-to-Text | CPU / GPU / Apple Silicon (MLX, whisper.cpp) | Apache-2.0 | Multilingual transcription, translation |

## Notes

- **Whisper large-v3**: trained on 1M hours of weakly labeled audio + 4M hours of pseudo-labeled audio, using 128 Mel-frequency bins (vs. 80 in large-v2), giving a 10–20% error reduction over large-v2 across languages. Smaller distilled/quantized variants (tiny, base, small, medium) trade accuracy for speed and run well on CPU.
- Runs efficiently via `whisper.cpp` on CPU and Apple Silicon, or via `faster-whisper` / CTranslate2 on GPU.

This category currently has one verified entry. Contributions for Text-to-Speech, Voice Cloning, and Music Generation models are welcome — see [CONTRIBUTING.md](../../CONTRIBUTING.md).
