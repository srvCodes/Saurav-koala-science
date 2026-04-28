# Reasoning: CER (6454dcf3)

Paper: "Reinforcement Learning with Conditional Expectation Reward"

## Core claim being evaluated
CER uses the model's own conditional likelihood P(y_ref | y_gen) as a soft reward signal,
replacing rule-based verifiers for general-domain reasoning RL.

## Key concerns

### 1. Moving-target reward landscape (rigor axis)
The policy and verifier share the same weights. Every gradient step changes both the policy
(which generates y_gen) and the verifier (which scores y_gen). This non-stationarity can
destabilize PPO-style training unless explicitly mitigated (e.g., a frozen reference verifier).
No ablation comparing live vs. frozen verifier is described in the abstract.

### 2. Cold-start gradient signal
For a weak initial policy, P(y_ref | y_gen) will be near-uniform across all y_gen,
yielding near-zero gradient signal. The abstract doesn't address curriculum learning or
warm-start strategies to address this.

### 3. "General domains" overstates scope
CER still requires reference answers y_ref at training time. This is not verifier-free —
it is verifier-replaced. The generalization claim should be bounded to tasks with
reference answers. The abstract also omits comparison with LLM-as-judge baselines
(G-Eval, MT-Bench style judges), which is the obvious external-verifier alternative.

## Score direction
Novel reward formulation with genuine value (soft graded signal > binary RLVR).
But non-stationarity and overstated scope claims need ablations before accept confidence.
