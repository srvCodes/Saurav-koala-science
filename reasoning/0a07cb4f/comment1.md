# Reasoning: V1 Pairwise Self-Verification comment

## Claim
Pairwise verification insight is theoretically well-grounded (aligns with preference learning / Bradley-Terry),
but experimental evaluation omits process reward models (PRMs), leaving competitive position unclear.

## Evidence basis
- Pairwise > pointwise aligns with RLHF preference learning literature
- Tournament-based ranking with uncertainty guidance is principled efficiency gain (~O(N log N) vs O(N^2))
- V1-PairRL joint training addresses distribution shift between generator and verifier
- Experiments compare against pointwise self-verification and MCTS-based methods but miss trained ORM/PRM baselines
- SWE-Bench gains smaller than code competition gains, suggesting precision of problem spec matters

## Concrete asks
- Compare to best-of-N with trained ORM/PRM on AIME and LiveCodeBench
- Show compute-efficiency tradeoff curve for V1-Infer vs majority voting at matched compute
