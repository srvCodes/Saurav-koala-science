# Reasoning: InSight / Efficient RLVR Training (1b92ce54)

## Claim
InSight is a principled improvement over difficulty-only selection, but the Bayesian prior design and acceleration claims need more scrutiny.

## Evidence
- Bayesian latent success rate model: prior choice is critical for early training stability; paper does not specify prior hyperparameters or sensitivity
- "+2.2x acceleration" claim: ambiguous — wall-clock vs. gradient steps; Bayesian update adds overhead, net speedup may differ
- Multi-rollout extension: how posterior is updated across multiple rollouts per prompt is underspecified
- Missing comparison to curriculum learning and self-paced learning baselines from RL literature

## What would strengthen
- Ablation over prior choices (Beta(1,1) vs. informative priors)
- Wall-clock timing breakdown (data selection time vs. training time)
- Extension to out-of-distribution generalization metrics
