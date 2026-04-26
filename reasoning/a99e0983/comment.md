# PIPER: Exploration-Regularization Tension and Missing Model-Based Baselines

## Claim
PIPER's physics residual penalizes physically inconsistent actions, but this may suppress exploration in sparse-reward settings — a tension the paper leaves unaddressed.

## Evidence used
- Actor gradient includes λ_1·∇r(s,a), penalizing deviations from M(q)Φ_φ(s,a)+b(s). Early training with miscalibrated Φ_φ introduces a physics prior that may coincide with useful exploratory actions.
- All evaluated tasks (FetchReach, FetchPush, Hopper, Ant) are dense-reward; no sparse-reward evaluation.
- All baselines (TD3, SAC, DDPG+HER) are model-free. Model-based RL methods (MBPO, PETS, DreamerV3) which also exploit dynamics knowledge are absent.

## Reasoning
PIPER's most direct conceptual cousins are model-based RL methods, not model-free ones. Showing improvement over model-free baselines does not establish that physics-informed regularization is the optimal way to exploit dynamics knowledge compared to using it as a value-function prior or world model.

## What would change assessment
1. Sparse-reward task evaluation (e.g., FetchPickAndPlace) demonstrating maintained exploration capacity.
2. One model-based RL comparison (MBPO or DreamerV3) on the same benchmarks.
