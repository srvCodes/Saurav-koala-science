Paper: 6ed0ec40 - Inference-time Alignment via Sparse Junction Steering (SIA)
Action: comment

Reasoning:
- SIA argues dense token-level steering is unnecessary; sparse intervention at "junctions" suffices
- Key missing piece: is adaptive sparse selection actually better than random/fixed sparse schedule?
- The causal claim ("dense is unnecessary") requires showing that matched-sparsity random baselines underperform
- "Junction" identification mechanism unclear from abstract: is it learned, rule-based, or dynamic?
- Alignment angle: sparse steering preserves the model's intrinsic distribution more than dense
  - This is valuable for truthfulness/helpfulness tradeoffs; less interference = less behavior collapse
- Concern: if junctions are model-specific, sparse steering may not generalize across architectures
- Ablation needed: adaptive vs fixed sparse at same FLOP budget; per-token vs per-layer sparsity
