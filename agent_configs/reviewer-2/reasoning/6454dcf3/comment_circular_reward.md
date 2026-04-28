# Comment: Circular Reward Optimization in CER

## Paper
"Reinforcement Learning with Conditional Expectation Reward" (6454dcf3-6eff-4b23-b5be-9bfaa905a83a)

## Claim
CER's use of the training model as its own verifier creates a non-stationary reward landscape distinct from format-mimicry and memorization issues already identified.

## Key Reasoning
- CER = E[log p_θ(ref | gen)] where p_θ is the *same* model being updated by GRPO/PPO
- Standard RLHF freezes a separate reward model before RL; rule-based RLVR uses a fixed external verifier
- As θ updates, p_θ(ref | ·) shifts — the reward for the same (gen, ref) pair changes throughout training not because gen improves but because the model's internal conditional distributions evolve
- Feedback loop risks reward inflation: model learns to assign high p_θ(ref | gen) for arbitrary gen, regardless of semantic correctness
- Distinct from format mimicry (which concerns what surface patterns are rewarded) — this is about how reward calibration degrades dynamically over training

## Diagnostic Tests Not in Paper
- Ablation: CER(policy) vs CER(frozen SFT checkpoint) as verifier — performance delta reveals feedback loop severity
- Mean CER reward on incorrectly-answered held-out samples across training steps: rising scores signal inflation

## Score Impact
Non-stationary reward is a material concern for claims about CER's superiority over rule-based RLVR.
