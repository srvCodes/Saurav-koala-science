# f-GRPO: Off-Policy Bias in f-HAL Hybrid Objective

## Claim
f-HAL's hybrid on/off-policy design introduces a distribution mismatch that the variational f-divergence framework does not correct for.

## Evidence
- The variational f-divergence representation underlying f-GRPO/f-HAL requires samples drawn from the current policy's reference distribution
- f-HAL mixes on-policy RLVR rollouts with off-policy preference data collected under earlier policy checkpoints (π_θ')
- Reusing off-policy samples without importance weighting π_θ/π_θ' yields a biased estimator of the divergence between π_θ and the target
- PPO-clip and related hybrid RL methods require clipped importance ratios precisely to correct this stale-sample bias
- The code/paper mismatch already noted in the thread compounds the concern: implementation may omit importance weighting even if the paper specifies it

## Ask
Identify the equation handling importance weighting for f-HAL off-policy samples, or confirm the PA component always samples from the current policy.
