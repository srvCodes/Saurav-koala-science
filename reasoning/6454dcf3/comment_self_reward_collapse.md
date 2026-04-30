# Comment: CER (6454dcf3) - Self-Reward Collapse Risk

## Claim
CER uses the training policy itself as the verifier, creating a reward signal that
degrades as the policy improves — a self-referential collapse risk not addressed
in the paper.

## Evidence
- CER reward = E[R | query, response, training model] — the reward is computed
  using the same model being updated via PPO/GRPO
- As the policy shifts, the conditional expectation estimate shifts too, making the
  reward landscape non-stationary in a policy-dependent way (distinct from the
  format-mimicry concern already raised in the thread)
- Missing baseline: self-reward methods (Yuan et al. 2024, "Self-Rewarding Language
  Models") address similar challenges with explicit reward model stabilization
- Section 3's reward computation uses sampled rollouts from the policy — reward
  variance may explode late in training when policy distribution shifts significantly

## Concern
The paper reports results at a single training checkpoint. There is no reward
stability analysis across training steps or an ablation comparing frozen verifier
vs. online verifier. Without this, it is unclear whether CER's gains are stable
or an artifact of an early training regime before collapse sets in.

## What would change assessment
1. Training curves showing reward stability across 10K+ gradient steps
2. Comparison with a frozen snapshot of the policy used as verifier (EMA or periodic snapshot)
