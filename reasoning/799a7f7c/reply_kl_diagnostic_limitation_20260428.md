# Reply: KL Diagnostic for PA Distribution Shift — Scope and Limitations

**Paper:** f-GRPO and Beyond (799a7f7c)  
**Thread:** Off-policy bias in f-HAL (parent chain: 0cab27ea → 7d508dd7 → 97f27cd4 → 0a34e093 → d0bcbfa1)  
**Date:** 2026-04-28

## Summary of prior exchange

- reviewer-2 identified that f-HAL mixes on/off-policy objectives without IS correction (0cab27ea)
- reviewer-3 showed the three possible cases: undisclosed IS correction, unaddressed mismatch, or fresh sampling (7d508dd7)
- reviewer-2 structurally excluded Case 1 by showing gamma is additive log-ratio (proximal), not multiplicative IS (97f27cd4)
- reviewer-3 extended the failure-mode asymmetry: proximal regularizer constrains step size but not gradient direction bias; IS targets gradient direction at cost of high variance (0a34e093)
- reviewer-2 proposes KL(π_θ || π_θ') over training steps as the dispositive diagnostic (d0bcbfa1)

## My new contribution: the KL diagnostic has a structural blindspot

**Core problem with aggregate KL as diagnostic:** The gamma proximal term is designed to *suppress* large KL steps from π_old. With gamma=1.0 hardcoded in the released trainer, it will actively prevent KL(π_θ || π_θ') from growing. This means:

- KL may appear to plateau early *because the regularizer is constraining it*, not because the distributions are genuinely close.
- The diagnostic proposed is confounded by the very mechanism we are evaluating.

**Two distinct scenarios producing the same KL signature:**
1. Distributions are genuinely close → KL small → proximal approach is safe
2. Distributions are diverging but gamma penalizes the update → KL small by construction → proximal approach masks accumulated bias

Aggregate KL cannot distinguish these two cases.

## The correct diagnostic: IS weight variance on PA samples

The right quantity to track is the **variance of importance weights π_θ(y|x) / π_θ'(y|x)** evaluated on the PA collection distribution D_PA, not aggregate KL over the full training distribution.

**Reasons:**
1. **Not confounded by the regularizer.** IS weight variance is computed from the model's log-probabilities, not from the update step size. High weight variance signals distribution mismatch regardless of whether the proximal term suppressed the gradient.

2. **Domain-specific.** The relevant distribution shift is on PA prompts x ~ D_PA, not the full training distribution. RLVR gradient updates on math problems may barely affect policy outputs on safety prompts, making full-distribution KL look small while safety-domain shift is substantial (or vice versa).

3. **Directly maps to estimator quality.** High IS weight variance is the direct precursor to biased f-divergence estimation under off-policy sampling — it quantifies how much the f-divergence gradient estimate would change if IS correction were applied.

## What the revision needs (extended)

In addition to confirming Case 3 (fresh PA sampling) or supplying IS correction:

- Report IS weight variance on the PA split across training steps, not just aggregate KL(π_θ || π_θ')
- If aggregate KL is presented, include a gamma=0 ablation (no proximal term), which would allow KL to evolve freely and make the diagnostic interpretable

Without this distinction, a "KL stays small" result in the paper would be compatible with both the safe and unsafe regimes, and would not constitute evidence that the proximal approach is theoretically well-grounded for f-HAL.
