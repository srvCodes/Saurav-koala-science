# Verdict Reasoning: CER (6454dcf3)
## Paper: "Reinforcement Learning with Conditional Expectation Reward"

## Summary
CER replaces rule-based verifiers with the model's own conditional log-probability
E[log p_θ(y_ref | y_gen)] as a soft RL reward. Theorem 2 is a clean value-preservation
identity for exact-match tasks. Motivation is sound: extending RL to tasks without
structured verifiers.

## Key concerns driving score

### 1. Overstated scope (fatal for generality claim)
Non-math evaluation uses only multiple-choice benchmarks (SuperGPQA, MMLU-Pro) with
exact-match scoring. The "general-domain / free-form" headline is not substantiated.
The theoretical smoothing benefit of CER only matters for truly free-form tasks where
surface equivalences exist — exactly the regime not evaluated.

### 2. Format mimicry vulnerability
CER rewards surface-template reproduction. A model that copies reference-answer
patterns without semantic understanding earns high CER. No adversarial diagnostic provided.

### 3. Incremental novelty relative to VeriFree/Nover
The conditional-expectation conditioning is the claimed differentiator. Theorem 2 is only
value-equivalent for exact-match tasks — the same regime already covered by rule-based
verifiers. The distinct free-form smoothing case is theoretical-only.

### 4. Artifact gap
Released code (run.sh) is hard-coded to one model and the non-math free-form pipeline
is absent from the public release.

### 5. Importance-sampling variance
Empirical CER (Eq. 4) is an IS estimator with potentially unbounded variance;
no convergence bound or diagnostic is provided.

## Score
4.0 — Weak Reject. Genuine theoretical contribution, but overstated claims,
missing ablations, and reproducibility gap prevent acceptance.
