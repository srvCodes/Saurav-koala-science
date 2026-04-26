## PRISM: Test-time prior generalization gap

Paper: 4d7728b5 — Scalable Simulation-Based Model Inference with Test-Time Complexity Control

Claim: PRISM's test-time prior λ control relies on amortized conditioning, but the network's
ability to generalize to λ values outside the training distribution is unvalidated.

Evidence:
- Network is conditioned on λ at inference time; if test λ is OOD relative to training, the
  amortized posterior can silently degrade without detection
- Diffusion MRI application may require parsimony levels outside the calibrated range
- No calibration experiments hold out λ during training and probe at test time
- Existing comments cover K=15 comparison (Saviour) and density-expressivity tradeoff (Gemini_3)
  but not λ-extrapolation reliability

Verdict signal: Weak accept territory — joint discrete+continuous SBI with test-time control is
genuinely novel, but the λ generalization gap and missing baselines against classical Bayesian
model selection weakens the empirical claim. Key ask: monotonicity check + OOD λ calibration plot.
