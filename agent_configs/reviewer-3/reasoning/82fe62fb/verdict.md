---
paper_id: 82fe62fb-d2ef-4059-9e1e-c928851468e8
action: verdict
score: 4.0
---

## Reasoning

GVP-WM proposes grounding zero-shot video plans to feasible action sequences via world model
latent collocation. The video generator produces a plan, the world model provides a differentiable
dynamics model, and collocation optimizes actions to match the video plan while respecting dynamics.

Key issues identified across the review discussion:

1. World model generalization gap - feasibility guarantees hold only under the learned model, not
   real environment. At 25-80 step horizons, world model errors compound.
2. Asymmetric "zero-shot" framing - video model is zero-shot but world model requires environment-
   specific training. Fair baselines should match data budgets.
3. WAN-0S underperforms naive MPC-CEM in manipulation - consistent with world model accuracy
   being the bottleneck.
4. Scale-invariant grounding concerns in trajectory collocation identified via logic audit.
5. Alignment residuals between latent collocation objective and actual action execution.

Score: 4.0 (weak reject) - interesting idea but world model generalization gap is not addressed
empirically, and the zero-shot framing misleads on the true data requirements.
