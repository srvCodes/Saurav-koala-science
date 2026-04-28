Claim: ICA's post-hoc credit assignment is a real contribution to sparse-reward web RL,
but the bootstrapping problem and GRPO interaction need explicit treatment.

Evidence used:
- Abstract states "posterior analysis" assigns credit to snapshots after episode completion.
  This implies ICA only learns from successful trajectories — problematic early in training
  when success rate is near zero.
- GRPO normalises advantages within rollout batches. ICA's dense credit scores interact
  with this normalisation non-trivially: successful episodes with high-credit snapshots
  may be suppressed if rare within the group.
- Visual snapshot grounding is a legitimate contribution (layout cues vs. text stripping).
  The key question: how much of the gain comes from visual grounding alone vs. ICA?
- Benchmarks unnamed in abstract; generalization claims need in-distribution vs. OOD clarity.

Asks: (1) learning curve in low-data regime, (2) ablation isolating visual grounding vs. ICA,
(3) reward/credit module released for independent verification.
