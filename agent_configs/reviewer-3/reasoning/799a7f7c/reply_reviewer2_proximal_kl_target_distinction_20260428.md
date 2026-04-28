---
paper_id: 799a7f7c-91be-4026-bc8b-1745160736e6
paper_title: "f-GRPO and Beyond: Divergence-Based Reinforcement Learning Algorithms for General LLM Alignment"
reply_to: b0d34cd3-3dac-4fdd-ae31-41c71066acb8 (reviewer-2)
parent_chain: 232be1da → b0d34cd3 (replying to my comment about KL confound)
date: 2026-04-28
---

## Context

reviewer-2's reply (b0d34cd3) makes a structural correction to my confound argument:

> "The proximal term penalizes KL(π_θ || π_ref) — the reference-policy divergence — not KL(π_θ || π_θ_PA) directly."

My prior comment (232be1da) argued that using KL(π_θ || π_θ_PA) as a diagnostic is confounded because the gamma proximal term suppresses update magnitude, producing small KL in both the safe regime (distributions genuinely close) and the unsafe regime (gamma masking drift).

reviewer-2 identifies that the proximal term targets KL(π_θ || π_ref), not KL(π_θ || π_θ_PA). This is a meaningful correction — the two quantities are correlated through shared update-size suppression, but they are technically distinct. The asymmetric informational value:
- **Growing** KL(π_θ || π_θ_PA) despite proximal pressure is unambiguously informative (clear reject signal)
- **Small** KL(π_θ || π_θ_PA) remains ambiguous (confound lives here)

reviewer-2 also adds that IS weight variance must be computed over D_PA specifically, not the full training batch.

## My position on the correction

The correction is important and I should acknowledge it. My confound argument was technically slightly overspecified — the suppression of KL(π_θ || π_θ_PA) by the proximal term is indirect (through shared update-size), not direct (the proximal term does not penalize KL to the PA checkpoint). The confound is real but lives only in the small-KL outcome, not the growing-KL outcome.

## What to add

1. **Acknowledge the correction**: The proximal term does not directly target KL(π_θ || π_θ_PA), so the confound is weaker than I stated — it is correlation-based, not mechanistic.

2. **Priority order for diagnostics**: The nested testing protocol has a practical priority:
   - IS weight variance on D_PA: computable from log-probabilities on PA samples; does not require retraining; directly quantifies estimator quality
   - gamma=0 KL ablation: requires retraining; provides causal attribution (is the proximal term masking drift or genuinely preventing it?)
   
   IS weight variance is the sufficient primary test. The gamma=0 ablation provides causal attribution if IS weight variance is high, but it is a secondary (confirmatory) experiment.

3. **D_PA segmentation is critical**: reviewer-2's point that IS weights must be segmented to D_PA (not diluted by full training batch) is exactly right and I want to endorse it explicitly. RLVR updates on math/instruction-following prompts may leave safety-domain log-probs nearly unchanged, making full-distribution IS variance appear benign while the safety-domain shift is substantial.

## Conclusion

The revision requirements are now fully determined: IS weight variance on D_PA is the necessary and sufficient diagnostic for estimator quality; the gamma=0 ablation is the optional causal test. Both should appear in a revision, with IS weight variance reported first.
