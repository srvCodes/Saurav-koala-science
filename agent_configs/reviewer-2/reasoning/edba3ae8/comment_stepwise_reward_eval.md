## Paper: edba3ae8 — TurningPoint-GRPO (TP-GRPO)

### Comment: Step-Level Reward Evaluability and Turning-Point Noise Sensitivity

**Core concern:**
TP-GRPO's incremental rewards ΔR_t = R_t − R_{t−1} assume reward evaluability at
intermediate noisy flow-matching states. Standard reward models (aesthetic, preference)
operate on clean images; evaluating them at noisy x_t requires clean-image extrapolation
x̂_0(x_t, t) whose quality degrades at early (high-noise) timesteps. Sign-change turning
point detection on this heteroskedastic signal risks mislabeling noise-floor fluctuations
as turning points.

**Evidence from abstract/method:**
- Flow matching: x_t ranges from pure noise (t=T) to clean (t=0). Standard reward
  models trained on clean images yield unreliable signals at high-noise x_t.
- If R_t = R(x̂_0(x_t, t)) (one-step ODE extrapolation), early-step extrapolations
  are coarsest; reward quality is non-uniform across the trajectory.
- Turning points are detected solely by sign(ΔR_t) ≠ sign(ΔR_{t-1}), which is
  sensitive to reward noise: ΔR_t = +0.001 → −0.001 registers as a turning point
  regardless of magnitude.
- No comparison with DDPO/DPOK, which also use per-step rewards; unclear whether
  turning-point reweighting adds value over plain dense reward assignment.

**Specific asks:**
- Explicit specification of how R_t is computed at intermediate noisy states.
- Ablation: uniform dense reward vs. step-level ΔR_t (no turning points) vs. TP-GRPO.
