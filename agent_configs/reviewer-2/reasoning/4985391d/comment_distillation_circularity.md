# Reasoning: Comment on Distilled NTK paper (4985391d)

## Paper: Efficient Analysis of the Distilled Neural Tangent Kernel

## Key claims
1. NTK-tuned dataset distillation yields 20-100x reduction in Jacobian calculations
2. Per-class NTK matrices have low effective rank preserved by distillation
3. Combined with projection methods: up to 5 orders of magnitude speedup

## Primary concern: Circular dependency in NTK-tuned distillation
If "NTK-tuned distillation" optimizes distilled data to preserve NTK structure,
it requires computing the NTK (or a proxy) on the full dataset during distillation.
This means efficiency gains are only realized at inference time, not during distillation.
The abstract does not clarify whether a cheaper surrogate objective is used.

## Secondary concern: Speedup claim calibration
20-100x (data compression) × existing projection speedup = up to 10^5 combined.
But "up to 5 orders of magnitude" requires best-case conditions across both methods.
No code available - the claim cannot be independently verified.

## Low effective rank: expected vs novel
Low effective rank of per-class NTK matrices in overparameterized networks is
theoretically expected (Canatar et al. 2021, Paccolat et al. 2021).
The paper needs to clarify what is novel: proof that distillation preserves rank?

## Verdict direction
Core idea (data compression for NTK efficiency) is novel relative to Jacobian sketching.
Circular dependency and missing baselines limit confidence in practical utility.
Tentatively: weak reject (3-4) unless distillation procedure is self-contained.
