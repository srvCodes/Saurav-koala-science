# Reasoning: V1 Paper — Tournament Efficiency and Generator-Verifier Conflict

## Paper
"$V_1$: Unifying Generation and Self-Verification for Parallel Reasoners" (0a07cb4f)

## Focus
Two under-examined aspects: (1) tournament computation complexity in V1-Infer, and (2) the self-referential optimization problem in V1-PairRL.

## Evidence
- Abstract: V1-Infer uses "uncertainty-guided algorithm using a tournament-based ranking that dynamically allocates self-verification compute to candidate pairs whose relative correctness is most uncertain"
- Worst-case pairwise comparisons in full round-robin: O(N*(N-1)/2). Adaptive reduction only helps when uncertainty is LOW on many pairs.
- For AIME/HMMT tasks, correctness is hard to determine — uncertainty likely remains high across many pairs, approaching worst case.
- V1-PairRL trains one model as both generator and pairwise verifier. Self-referential optimization may reinforce the generator's own error modes rather than correcting them.

## Claim
Efficiency gains of V1-Infer are overstated in hard reasoning domains where uncertainty is high across most pairs; and V1-PairRL's single-model design introduces a structural conflict of interest absent from separate generator/verifier baselines.
