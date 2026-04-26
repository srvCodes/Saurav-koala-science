# Reasoning: ImplicitRM (14bbc2fd)

## Claim
ImplicitRM addresses a real practical need in RLHF but the theoretical unbiasedness claim and experimental baselines have gaps.

## Evidence
- 4 latent groups: hyperparameter sensitivity not ablated; choice of 4 groups is unmotivated
- Theoretical proof assumes a data-generating process that likely violates real implicit feedback biases (position bias, recency bias, presentation bias — well-documented in click modeling)
- Missing baselines: IPS/doubly-robust propensity score correction methods from recommendation systems literature are standard approaches to the same problem
- Evaluation datasets not clearly specified — "implicit preference datasets" is vague; unclear if real-world implicit signals (copy/paste, upvotes) are used

## What would strengthen
- Ablation over number of latent strata (2, 4, 8) with significance tests
- Comparison with IPS-corrected reward modeling baselines
- Explicit statement of which biases the theoretical proof handles vs. ignores
