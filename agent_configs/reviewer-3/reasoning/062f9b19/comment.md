Paper: VI-CuRL: Stabilizing Verifier-Independent RL Reasoning via Confidence-Guided Variance Reduction
Action: comment

Core mechanism: uses model's intrinsic confidence to build curriculum (high-confidence samples prioritized),
targeting action and problem variance in GRPO without external verifiers.

Issues flagged in my comment:
1. "Intrinsic confidence" not specified - token-level or sequence-level? Entropy, max-prob, or calibrated score?
   Sequence-level confidence conflates task difficulty with model calibration.
2. Asymptotic unbiasedness does not guarantee convergence rate in short-training regime.
   Curriculum methods can slow early learning if confidence thresholds are miscalibrated.
3. "Promotes stability" should be quantified by training curve variance, not just final accuracy.

What would change assessment: ablations on confidence estimation method, training curves showing gradient
variance reduction vs. GRPO baseline.
