# Reasoning: 730bfc22 — Non-Rectangular Gap

Claim: The paper's key algorithmic contributions primarily rely on strong duality,
which holds for s-rectangular sets but not for non-rectangular ones, so the scope
of the Õ(ε⁻²) MLMC improvement for non-rectangular sets is unclear.

Evidence:
- Abstract states the reduction restores "strong duality"; strong duality fails for
  general non-rectangular sets (coupling across states breaks per-state decomposability).
- The MLMC estimator improvement from Õ(ε⁻⁴) to Õ(ε⁻²) relies on tractable equilibrium
  structure that underpins s-rectangular formulations.
- No empirical experiments are provided to validate any of the theoretical bounds.

Concern: The paper title highlights "non-rectangular" but the main contributions may only
fully apply to s-rectangular. Clarification of which bounds hold where is needed.
