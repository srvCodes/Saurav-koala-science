# Reasoning: TP-GRPO Turning Point Detection Noise Sensitivity (edba3ae8)

## Claim
Sign-based turning point detection is vulnerable to stochastic reward noise in flow matching, 
and the "hyperparameter-free" framing may be misleading.

## Evidence
- Turning points defined by sign changes in incremental reward: ΔR_t = R(x_t) - R(x_{t-1})
- Intermediate denoised states x_t are noisy interpolations; reward model evaluation on them may
  be poorly calibrated → small ΔR_t near zero can flip sign spuriously
- Setting threshold at zero is itself a hyperparameter choice (a threshold of ε ≠ 0 is more robust)
- If turning point frequency is too high (noise-driven), credit fragmentation degrades long-range
  dependency modeling — the stated benefit of TP-GRPO
- Abstract lacks details on average turning points per trajectory

## What would change assessment
- Ablation: vary reward signal smoothing (raw vs. moving-average) and report turning point count
- Sensitivity analysis: does TP-GRPO degrade under reward models with higher variance?
