# Ornith 9B Tapsin

Fine-tuned **Ornith 1.5 9B** models with extended context windows (64K and 128K tokens), optimized for long-context reasoning, coding, and creative tasks.

## 📦 Model Variants

| Variant | Context Window | Size | Quantization |
|---------|----------------|------|--------------|
| `ornith-9b-tapsin:64k` | 65,536 tokens | ~5.6 GB | Q4_K_M |
| `ornith-9b-tapsin:128k` | 131,072 tokens | ~5.6 GB | Q4_K_M |

Both variants share the same base weights and mmproj (multimodal projector), differing only in context window configuration.

## 🚀 Quick Start with Ollama

### Pull from Hugging Face (GGUF)

```bash
# 64K context variant
ollama pull hf.co/tapsin/ornith-9b-tapsin:64k-Q4_K_M

# 128K context variant
ollama pull hf.co/tapsin/ornith-9b-tapsin:128k-Q4_K_M
```

### Or build locally from Modelfiles

```bash
# Build 64K variant
ollama create ornith-9b-tapsin:64k -f https://huggingface.co/tapsin/ornith-9b-tapsin/raw/main/Modelfile-64k

# Build 128K variant
ollama create ornith-9b-tapsin:128k -f https://huggingface.co/tapsin/ornith-9b-tapsin/raw/main/Modelfile-128k

# Run
ollama run ornith-9b-tapsin:64k
ollama run ornith-9b-tapsin:128k
```

## 💻 Usage Examples

### Long Context Chat
```bash
ollama run ornith-9b-tapsin:128k "Summarize this 100-page document: <paste long text>"
```

### Code Analysis
```bash
ollama run ornith-9b-tapsin:64k "Review this codebase for bugs: <paste large code files>"
```

### Creative Writing
```bash
ollama run ornith-9b-tapsin:128k "Write a novel chapter continuing from: <long story context>"
```

## 🤗 Hugging Face Repository

**Model Hub:** [https://huggingface.co/tapsin/ornith-9b-tapsin](https://huggingface.co/tapsin/ornith-9b-tapsin)

Files available on Hugging Face:
- `ornith-9b-tapsin-Q4_K_M.gguf` — Main model weights (Q4_K_M quantization, ~5.6 GB)
- `ornith-9b-tapsin-mmproj.gguf` — Multimodal projector (for vision tasks, ~624 MB)
- `Modelfile-64k` — Ollama modelfile for 64K context
- `Modelfile-128k` — Ollama modelfile for 128K context

## 📜 License

**MIT License** — Free for commercial and personal use.

```
MIT License

Copyright (c) 2026 tapsin

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

## 🙏 Support / Donate

If you find these models useful, consider supporting development:

- **GitHub Sponsors:** [https://github.com/sponsors/tapsin](https://github.com/sponsors/tapsin)
- **Ko-fi:** [https://ko-fi.com/tapsin](https://ko-fi.com/tapsin)
- **Patreon:** [https://patreon.com/tapsin](https://patreon.com/tapsin)
- **BTC:** `bc1qxxxx...` (add your address)
- **USDT (TRC20)**: `TYCK6ZyMS6UDt787foPH2QwFuvkdqMw1Jv`
- **USDT (BSC20)**: `0x15aac92a1945ddbe5c79304bfa388d6be99b26a3`

## 🔧 Technical Details

### Base Model
- **Architecture:** Llama 3.1 / Ornith 1.5 9B
- **Original:** [Ornith-1.5-9B](https://huggingface.co/collections/kietaskrutas01/ornith-15-9b-673b4d7c5b3f2d3a3c4d5e6f)
- **Fine-tuning:** Extended context via RoPE scaling (YaRN/PI)

### Quantization
- **Method:** Q4_K_M (4-bit K-means quantized, medium)
- **Size:** ~5.6 GB (model) + ~624 MB (mmproj)
- **Quality:** Near-lossless for 9B parameters

### Context Extension
- **64K:** YaRN scaling factor ~2.0
- **128K:** YaRN scaling factor ~4.0
- **Technique:** NTK-aware RoPE scaling with dynamic NTK alpha

### Hardware Requirements
| Context | VRAM (GPU) | RAM (CPU offload) |
|---------|------------|-------------------|
| 64K     | ~8 GB      | ~12 GB            |
| 128K    | ~12 GB     | ~18 GB            |

With `--ngl 999` (full GPU offload), VRAM scales with context length due to KV cache.

## 📁 Repository Structure

```
ornith-9b-tapsin/
├── Modelfile-64k                       # Ollama modelfile for 64K ctx
├── Modelfile-128k                      # Ollama modelfile for 128K ctx
├── README.md                           # This file
└── LICENSE                             # MIT License
```

> **Note:** Model weights (`.gguf` files) are hosted on [Hugging Face](https://huggingface.co/tapsin/ornith-9b-tapsin) due to GitHub's file size limits. Use the Ollama pull commands above or reference the Modelfiles directly from HF.

## 🔗 Links

- **GitHub:** [https://github.com/tapsin/ornith-9b-tapsin](https://github.com/tapsin/ornith-9b-tapsin)
- **Hugging Face:** [https://huggingface.co/tapsin/ornith-9b-tapsin](https://huggingface.co/tapsin/ornith-9b-tapsin)
- **Ollama Library:** (pending submission)
- **Base Model (Ornith 1.5 9B):** [https://huggingface.co/kietaskrutas01/Ornith-1.5-9B-uncensored-GGUF](https://huggingface.co/kietaskrutas01/Ornith-1.5-9B-uncensored-GGUF)

---

*Built with ❤️ for the open-source AI community*