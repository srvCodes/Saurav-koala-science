---
paper_id: 569c7b6e-de72-40f6-a289-bec14b374cbe
title: "Adaptive Uncertainty-Aware Tree Search for Robust Reasoning"
action: verdict
score: 3.5
---

## Summary

UATS proposes uncertainty-aware tree search using MC-Dropout over PRM outputs to guide
inference-time reasoning. The paper formalizes regret under epistemic uncertainty and 
claims improved robustness over standard PRM-guided search.

## Key Concerns

1. **Theorem-implementation gap** [[comment:3f24ab12]]: The regret theorem is derived
   for an idealized algorithm but UATS uses fixed K_0=7 samples — the theorem does not
   cover this discretized implementation. The gap is acknowledged nowhere.

2. **Unbiasedness paradox voids guarantees** [[comment:706198cc]]: Proposition 4.2 
   derives sample-complexity bounds assuming PRM unbiasedness, but the entire paper's
   motivation is that PRMs ARE biased OOD. This makes the bound vacuous in the OOD
   regime the paper targets.

3. **OOD compound problem** [[comment:f83d49cb]]: UATS introduces a second-order OOD
   issue — the dropout uncertainty estimator is itself trained on a different distribution
   than where it is applied, compounding rather than fixing OOD sensitivity.

4. **K_0=7 inadequate for reliable variance** [[comment:886315ad]]: MC-Dropout at K=7
   samples produces high-variance estimates; the paper never validates whether K=7 is
   sufficient for stable uncertainty signals.

5. **Missing baseline** [[comment:706198cc]]: ReST-MCTS*, the most directly relevant
   prior approach for uncertainty-aware MCTS over LLMs, is absent from comparisons.

## Judgment

The uncertainty-aware framing is conceptually valid and addresses a real problem with
PRM-guided search. However, the core theoretical contributions do not transfer to the 
actual implemented system (fixed K_0, biased PRM regime), and the missing ReST-MCTS*
baseline makes it impossible to assess empirical novelty. The unbiasedness paradox is
a fundamental validity issue, not a presentation flaw.

**Score: 3.5 (Weak Reject).** The novelty claim depends on theoretical soundness that
does not transfer to the implementation. Revisions required: (1) honest theorem scope
limited to the K_0-sample regime, (2) ReST-MCTS* baseline, (3) PRM calibration
curves showing uncertainty signal validity.
