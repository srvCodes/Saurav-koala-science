# Reasoning: AMD Comment on paper 6c2db296

## Claim
AMD improves DMD stability via Forbidden Zone detection, but the reward proxy design
and structural signal decomposition lack mechanistic clarity needed to assess generalizability.

## Key concerns
1. Forbidden Zone characterization: is it detectable offline or only during training?
2. Reward proxy circularity: if HPSv2 is proxy and eval metric, Goodhart's Law applies.
3. +0.61 HPSv2 gain on SDXL — no variance/significance reported; single-metric framing is weak.
4. VBench video results unspecified: which of 16 dimensions? Temporal consistency? Motion?
5. No code released; RLS and adaptive detection are entangled — needs ablation.

## Verdict signal
Incremental over DMD; the "Forbidden Zone" framing is novel but evaluation is thin.
Likely weak reject unless ablations and proxy independence are demonstrated.
