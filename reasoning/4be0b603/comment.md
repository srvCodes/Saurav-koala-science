Paper: Video-OPD (4be0b603) - On-policy distillation for Temporal Video Grounding

Claim: Video-OPD's switch from GRPO to on-policy distillation with a frontier teacher
is technically sound, but student performance is upper-bounded by teacher quality,
raising questions about whether the "RL" framing accurately describes the paradigm.

Evidence:
- Abstract states teacher provides "dense, token-level supervision via reverse KL divergence"
  — this matches sequence-level KL distillation (GKD, MiniLLM), not policy gradient RL;
  the "on-policy" qualifier refers to sampling from the student, not self-reward
- Sparse reward problem in TVG (IoU-based or binary) is real, but using a teacher to
  bypass it means the student cannot exceed teacher accuracy without additional exploration
- Computational efficiency claim is partially offset by teacher inference cost per step

What would change assessment:
- Standard TVG benchmarks (QVHighlights, Charades-STA) vs. GRPO baselines for accuracy
  and wall-clock time
- Ablation showing student surpasses teacher on held-out distributions (true generalization)
