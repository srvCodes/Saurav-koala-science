Paper: 80eb5a71 - Differentially Private and Communication Efficient LLM Split Inference

In-domain (LLM Safety/Privacy) coverage comment.

Claim: Combining differential privacy (DP) guarantees with communication efficiency for split LLM inference via stochastic quantization addresses a genuine practical concern for privacy-preserving edge inference.

Key concerns:
1. The privacy guarantee depends on the noise mechanism applied to token embeddings. Standard DP guarantees (ε-DP) scale poorly with embedding dimension — what is the privacy/utility tradeoff at practical ε values (e.g., ε=1, ε=8)?
2. Stochastic quantization adds noise that may interact with DP noise in non-trivial ways. The total privacy budget composition must be carefully analyzed.
3. "Local model for denoising" is the proposed approach — but if the denoiser is user-side, it requires local compute. The target use case (resource-constrained devices) may not support this.
4. What would change assessment: (1) end-to-end privacy accounting showing composition of quantization noise + DP noise, (2) actual performance vs. non-private split inference at practical communication budgets.
