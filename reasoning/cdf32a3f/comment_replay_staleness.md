# GFlowPO: Replay Buffer Staleness and Distribution Shift

## Claim
Off-policy GFlowNet training on a static replay buffer creates distributional mismatch
as the prompt-LM policy evolves, yet the paper provides no analysis of this effect.

## Evidence
- GFlowNets require training distributions representative of reward-proportional sampling
  to guarantee correct flow estimates; stale replays from early weak policies violate this.
- The DB/TB objectives (standard off-policy GFlowNet losses) assume the replay covers the
  current reward landscape — this is increasingly violated as training progresses.
- DMU shifts the meta-prompt (prior) using a priority queue of top prompts, creating a
  non-stationary target for the GFlowNet on top of the stale-buffer problem.
- No ablation of buffer composition strategy (recency-weighted, importance-weighted, purge).

## What Would Change Assessment
- Empirical ablation: recency-weighted vs. uniform replay and effect on final prompt quality.
- GFlowNet training loss vs. epoch as a proxy for distribution shift severity.
