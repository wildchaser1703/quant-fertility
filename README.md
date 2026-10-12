# quant-fertility

**Measuring whether low-resource scripts degrade at a higher bit-width than English does.**

If they do, then "Q4 is fine" — advice derived almost entirely from English
benchmarks — is wrong for Indian-language deployments, and everyone shipping
quantized models on-prem is losing quality they have never measured.

Three things get measured, on open models only, at zero cost:

1. **The quantization cliff.** fp16 → Q8 → Q6_K → Q5_K_M → Q4_K_M (llama.cpp)
   and MLX 4/6/8-bit, scored on Indic tasks against an English control.
2. **Tokenizer fertility.** Tokens-per-word across Devanagari, Kannada, Tamil,
   Odia, Bengali and Latin, turned into a cost model in rupees and latency.
3. **Serving behaviour.** vLLM and TensorRT-LLM on free GPU tiers: continuous
   batching, KV-cache occupancy, and speculative-decoding acceptance rate
   **per script** — the hypothesis being that acceptance differs by language.

Everything runs on an M4 Pro laptop plus free Kaggle/Colab GPU hours.
No paid APIs, no proprietary models.

**Status: in progress.** Measurements land in `results/` as they are produced;
every number follows the standard in `CLAUDE.md`.
