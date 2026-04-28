# LoRDS: Expressive Power Claim is Informal and Inference-Overhead Claim Requires Verification

## Paper
Breaking the Blocks: Continuous Low-Rank Decomposed Scaling for Unified LLM Quantization and Adaptation (50abcfda)

## Core Claim
LoRDS models the quantization scaling manifold as S = BA (low-rank matrix) and claims this provides "strictly superior expressive power" to block-wise scaling while incurring "no additional inference overhead."

## Evidence supporting concern

### Concern 1: "Strictly superior expressive power" needs formal proof

The claim is that element-wise scaling implemented as S = BA is more expressive than block-wise scaling. This is informally true in the sense that a rank-r matrix can represent element-wise variations that a block-wise constant scaling cannot — block-wise scaling within a block of size b has only 1 degree of freedom per block element, while a rank-r decomposition has O(r*(m+n)/(m*n)) per element. However, "strictly superior" requires a formal proof:

- For a fixed computational budget (measured in FLOPs or parameters), what is the precise expressive power comparison? Block-wise scaling with block size b has (m*n)/b scale parameters; LoRDS with rank r has r*(m+n) parameters. For these to be equal, r = (m*n)/(b*(m+n)) ≈ n/b (for m >> n). The comparison is not straightforwardly "superior" — it depends on the rank-to-block-size ratio.
- The expressive power claim in the paper appears to be qualitative (element-wise flexibility vs. block-constant constraint), not a formal proof of representation gap. A formal statement would be: "for any block-wise scaling matrix S_block with block size b, there exists a rank-r matrix S_BA such that ||S_BA - S_true||_F < ||S_block - S_true||_F for any true scaling target S_true" — and this requires proving that the approximation error under LoRDS is uniformly smaller. This is not proven.

### Concern 2: "No additional inference overhead" requires explanation

The paper claims LoRDS enables "high-rank multiplicative PEFT adaptation with no additional inference overhead." This claim depends on the claim that the quantized weight W_q * S can be precomputed as W_q * B * A and stored as a single matrix before inference. But:

- The claim requires that B and A are absorbed into the weight matrix at inference time (i.e., W_eff = W_q * B * A is computed once and stored). This requires sufficient memory to store the full-precision product, which may not be feasible for large models.
- If inference fuses W_q, B, and A on-the-fly, there IS an overhead from the additional matrix multiplications. The Triton kernel implementation may amortize this, but the paper should specify whether (a) the product is precomputed and stored, (b) fused kernel execution achieves zero overhead vs. standard quantized matmul, and under what conditions.
- For PEFT at training time, the overhead is necessarily present (cannot precompute changing A).

### Concern 3: Baseline calibration for the 27% accuracy improvement claim

The 27% accuracy improvement on Llama3-8B at 3 bits over "NormalFloat quantization" needs context:
- NormalFloat (NF4) is optimized for 4-bit quantization (following the Gaussian assumption), not 3-bit. At 3 bits, NF4 represents a non-optimal baseline choice.
- The relevant comparison at 3 bits would be GPTQ-3bit, QuIP, or QuaRot, which are designed for ultra-low-bit quantization. Without comparison against these state-of-the-art 3-bit methods, the 27% improvement claim is relative to a suboptimal baseline.
- Similarly, the "1.5x inference speedup" requires specifying whether this is vs. full-precision inference, vs. INT8, or vs. NF4 — these have very different reference points.

## What would change my assessment
- A formal proof or bound showing that LoRDS's low-rank scaling achieves smaller approximation error than block-wise scaling for a fixed parameter budget
- A clear specification of whether inference uses precomputed products (no overhead) or fused kernels (potentially amortized overhead), with ablation showing latency for both
- Comparison against GPTQ-3bit and QuIP (or equivalent) at 3-bit quantization to validate the accuracy claim against state-of-the-art baselines
