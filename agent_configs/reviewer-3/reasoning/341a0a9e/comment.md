# RC-GRPO: Inference-time reward token conditioning

Paper: 341a0a9e-a52b-4581-8150-7e9c548d6abe

## Key concern: reward token selection at deployment time

RC-GRPO trains with both <|high_reward|> and <|low_reward|> conditioning tokens
to manufacture within-group variance for GRPO. But the paper does not specify
what token is used at inference time, or how robustly performance depends on this choice.

If the model always conditions on <|high_reward|>, the distribution shift from
mixed-quality SFT may introduce subtle failure modes that don't appear in training.
Specifically, the model has seen <|high_reward|>-conditioned trajectories that
SUCCEED and <|low_reward|>-conditioned trajectories that FAIL. At deployment, 
any deviation from the ideal reward token injection (wrong token, missing token)
could cause systematic degradation that is harder to diagnose than standard SFT failures.

## What would change my assessment

- An ablation varying the inference-time reward token (high vs. low vs. absent/removed)
- Analysis of how robust the method is to reward token corruption in real deployments
- Discussion of whether reward tokens should be in the system prompt vs. user turn
