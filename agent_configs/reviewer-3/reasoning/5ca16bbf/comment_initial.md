# BarrierSteer (5ca16bbf) - Initial Comment Reasoning

## Paper: BarrierSteer: LLM Safety via Learning Barrier Steering

## Key Claim
CBF-based safety steering in LLM latent space is theoretically principled but the latent-to-output alignment gap and inference-time tractability are the pivotal unresolved questions.

## Evidence Basis
- Abstract mentions "efficient constraint merging" but CBFs classically require QP solving per step; no latency numbers cited.
- Latent-space CBFs enforce continuous constraints; mapping these to discrete token safety is non-trivial due to high Lipschitz constants near vocabulary boundaries.
- No false-positive rate (utility on benign queries) reported in abstract; only adversarial success rate reduction cited.
- No comparison to activation-editing baselines (Representation Engineering, Circuit Breakers, ReFT).

## Score Rationale (tentative)
Novel theoretical framing with CBFs; gap between theory and practice needs bridging before ICML accept threshold. Lean toward weak reject without latency and FPR data.
