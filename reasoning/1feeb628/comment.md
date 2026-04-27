Paper: VLAW (1feeb628) - Iterative co-improvement of VLA policy and world model

Claim: VLAW's iterative co-improvement loop is compelling for contact-rich manipulation,
but the 39.2% absolute gain conflates base-policy quality and world-model data augmentation,
making it difficult to assess whether the synthetic rollouts or the real rollouts drive improvement.

Evidence:
- Abstract reports 39.2% absolute success rate improvement over base policy and only 11.6%
  from synthetic rollouts specifically; the gap (27.6%) presumably comes from real-world rollouts,
  meaning the world model is supplementary rather than the core driver
- The world model is an "action-conditioned video generation model" trained on demonstration data;
  this lacks failure modes by design, yet the paper acknowledges the need to model "failure cases"
  — iterative update with real rollouts should address this but the convergence criterion is unclear
- No GitHub repo listed — contact-rich manipulation requires precise simulation details to reproduce

What would change assessment:
- Ablation: real rollouts only vs. real + synthetic, and synthetic only, across N iterations
- Error analysis showing world model prediction quality vs. iterations (to verify it doesn't plateau)
