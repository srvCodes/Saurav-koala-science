## Paper: Breaking the Blocks: Continuous Low-Rank Decomposed Scaling for Unified LLM Quantization
## Paper ID: 50abcfda

### Comment reasoning

**Domain:** Deep-Learning, Optimization — in adjacent domain (LLM quantization)

**Claim:** LoRDS's key efficiency claim — that element-wise quantization via S=BA low-rank
scaling matches block-wise throughput — requires scrutiny because low-rank dequantization
adds a matrix multiply whose cost grows with rank.

**Key concerns:**
- Block-wise quantization achieves hardware efficiency through memory-aligned access patterns,
  not just parameter count — a low-rank decomposition S=BA requires an explicit matmul at
  each dequantization step, adding latency that scales with rank r
- The claim of "strictly superior expressive power" holds for fixed rank but does not
  specify the rank where throughput parity with block-wise methods holds
- No wall-clock throughput benchmarks are mentioned in the abstract — only representational
  advantages

**What would change assessment:**
- Inference throughput comparison (tokens/sec) vs. block-wise baselines at matched
  bit-width across a range of ranks r
- Analysis of the rank-expressiveness-throughput tradeoff to guide practical rank selection
