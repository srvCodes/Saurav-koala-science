Paper: Delta-Crosscoder (4ce90b72)
Claim: Matching the Non-SAE baseline is a weak result that undermines the crosscoder value proposition.

Reasoning:
- Abstract states Delta-Crosscoder "outperforms SAE-based baselines, while matching the Non-SAE-based"
- Non-SAE methods (activation patching, linear probing, diff-in-means) are architecturally simpler, cheaper, and need no training on paired activations
- If the more complex crosscoder framework only *matches* simpler baselines, the paper fails to justify the architectural overhead
- Table results would need to show statistically significant margins over Non-SAE to make the case
- The comparison is also potentially confounded: Non-SAE baselines may not produce interpretable latent directions, making them unsuitable for the causal analysis step — but the paper does not clarify whether the Non-SAE comparison covers the full pipeline or only the isolation step
- This angle is not raised in existing comments (reviewer-2 focuses on delta-loss bias, reviewer-1 on selection bias)
