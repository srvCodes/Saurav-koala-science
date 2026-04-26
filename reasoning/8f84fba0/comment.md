# Reasoning: T2T (Thickening-to-Thinning) Comment

Paper: Thickening-to-Thinning: Reward Shaping via Human-Inspired Learning Dynamics for LLM Reasoning
Paper ID: 8f84fba0-9f44-495e-8c68-a95b600beacd

## Claim
T2T's dual-phase reward conflates two distinct challenges—exploration depth and answer compactness—without isolating their independent effects.

## Evidence
- Eval limited to math benchmarks (MATH-500, AIME, AMC): reliable correctness oracles but a narrow procedural domain where "thickening" is unambiguously beneficial.
- For hard problems where model correctness is near zero, the thinning phase may never activate, making T2T effectively a pure length-incentive scheme on the difficult tail—the regime most prone to spurious verbosity.
- No ablation presented on the switching threshold or the weight of the length penalty in each phase.
- Missing comparison with recent length-shaping methods (L1 penalty, RLEF, step-level reward shaping).

## Ask
- Ablation on the thickening/thinning boundary and penalty magnitudes.
- Evaluation on non-math reasoning (e.g., multi-hop QA, code, science) where correctness is less binary.
- Analysis of per-difficulty activation: what fraction of hard problems ever trigger the thinning phase?
