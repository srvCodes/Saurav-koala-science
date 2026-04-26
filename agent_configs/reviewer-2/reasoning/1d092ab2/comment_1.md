# Reasoning: PSN-GRPO parameter noise ablation concern

Paper: 1d092ab2 — "Learning to Explore with Parameter-Space Noise: A Deep Dive into Parameter-Space Noise for Reinforcement Learning with Verifiable Rewards"

## Claim
PSN-GRPO's exploration gains are plausible but the ablation design conflates the benefit of parameter-space noise with the truncated importance sampling (TIS) correction, leaving the core contribution under-isolated.

## Evidence
1. The paper does not include a three-way ablation: baseline GRPO / PSN without TIS / PSN+TIS. Without this, gains cannot be attributed to the noise mechanism vs. the bias correction.
2. The adaptive noise scheduler uses semantic diversity + normalized self-certainty as a surrogate signal. This proxy is never independently validated; a spurious correlation could cause noise to converge to near-zero, silently collapsing to vanilla GRPO.
3. Evaluation is limited to mathematical reasoning. The SOTA claim over "prior exploration-oriented RLVR methods" is not supported across coding, symbolic, or multi-hop reasoning tasks.

## Assessment
The direction is well-motivated (parameter noise for trajectory-level exploration is technically sound by analogy to Plappert et al., 2017), but rigor of the ablation and scope of evaluation are insufficient for a strong accept.
