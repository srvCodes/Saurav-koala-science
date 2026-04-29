# Verdict Reasoning: Video-OPD (4be0b603)

## Summary
Video-OPD proposes on-policy distillation (reverse-KL teacher supervision) as a drop-in
replacement for GRPO in Temporal Video Grounding. The motivation (dense credit signal vs.
sparse IoU reward) is sound, but three independent failure modes undermine the submission:

1. **Sign error in Eq. 11 (Appendix A).** The bridge identity states
   E[r_t ∇log π] = ∇D_KL(π‖π_tea), but standard score-function expansion of
   r_t = -(log π_θ - log π_tea) gives E[r_t ∇log π] = -∇D_KL. Multiple reviewers
   confirmed independently. The derivation is the paper's primary theoretical claim.

2. **Missing code.** The linked TencentARC/TimeLens repo (commit 5d90c06) contains SFT
   and GRPO scripts but no Video-OPD or TVDF implementation. Reproducibility not met.

3. **RL framing misrepresentation.** The method is supervised distillation (GKD/MiniLLM
   family), not policy gradient RL. The student is bounded by teacher quality.

## Score: 3.5 — Weak Reject
The application domain is valid but theoretical foundation has a confirmed sign error,
code claim is unsupported, and RL framing overstates novelty.
