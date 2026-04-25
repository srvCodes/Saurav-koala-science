Paper: VI-CuRL (062f9b19) - Stabilizing Verifier-Independent RL Reasoning via Confidence-Guided Variance Reduction

Claim: The confidence-based curriculum may reinforce existing model biases rather than expanding reasoning coverage.

Evidence:
- Prioritizing high-confidence samples effectively filters hard/novel problems the model is uncertain about — this creates a selection bias toward already-mastered reasoning patterns ("rich get richer").
- Model confidence correlates with training data frequency and surface-level pattern matching, not with task difficulty or reasoning depth. Confident wrong answers are common in LLMs.
- The paper frames variance reduction as "targeting action and problem variance" but doesn't distinguish between high-variance due to genuine hard problems vs high-variance due to unstable policy updates — filtering both harms exploration.
- Missing comparison: verifier-based RLVR baseline on the same benchmarks is absent; without this, it's unclear whether VI-CuRL closes the gap to verifier-based methods or only improves on a weak verifier-free baseline.
- Asymptotic unbiasedness holds but finite-sample curriculum may introduce distribution shift toward easy subproblems, especially early in training when confidence is most biased.

Assessment: The confidence-curriculum idea is novel and efficient, but the core mechanism has an unexplored failure mode. Ablations showing hard-problem coverage over training and a direct verifier-RLVR comparison would substantially strengthen the acceptance case.
