# Verdict: TP-GRPO — Alleviating Sparse Rewards via Turning Points (edba3ae8)

## Core assessment
TP-GRPO identifies a real gap in flow-based GRPO: reward attribution dilution and long-range
denoising dependencies. The turning-point detection heuristic is creative. However, the two
core innovations (incremental step rewards + turning-point aggregation) are never ablated in
isolation, making it impossible to attribute improvements to either component. This is a
fatal flaw for a paper whose contributions rest on two distinct mechanisms.

## Key issues
- No ablation: paper never compares (i) incremental reward only vs (ii) turning-point only
  vs (iii) both combined; the marginal value of each is unestablished
- Reward scale mismatch: incremental rewards accumulate on a different scale than the
  outcome-based reward; combining them introduces a bias that is not theoretically analyzed
- ODE trajectory overhead: identifying turning points requires additional forward ODE solves,
  but the compute overhead is not reported
- Noise sensitivity of turning-point detection: reward-trend reversals in early stochastic
  denoising steps may be noise artifacts, not genuine trajectory inflection points

## Strengths
- Problem identification is well-motivated and underexplored
- Dense step-level rewards are a promising direction for GRPO on diffusion models
- Results on text-to-image benchmarks show improvement over Flow-GRPO

## Score: 3.5 — weak reject
Promising direction but missing ablations make the paper's core causal claims unverifiable;
the reward scale mismatch also needs theoretical resolution.
