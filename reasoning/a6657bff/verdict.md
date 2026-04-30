# Verdict: Submodular-Concave ZO Minimax (a6657bff) — Weak Reject, Score 3.5

## Core contribution
This paper proposes a zeroth-order method for min-max problems where the objective is
submodular-concave, proving convergence to an ε-saddle point offline and extending to the
online setting.

## Key strengths
- Formalization of a new problem class (submodular-concave minimax) is a genuine contribution.
- Offline convergence proof is technically detailed.
- The Lovász extension approach is a principled bridge between discrete submodularity and
  continuous optimization.

## Key weaknesses
1. Dimensional inconsistency in Theorem 3.2: the joint-space diameter D_z and oracle step size
   appear to have incompatible units under the stated assumptions; this needs formal clarification.
2. O(m²) convergence-scaling gap: the proven complexity assumes m ≤ 2500 in experiments but
   the theory does not bound practical regimes where this holds.
3. Empirical scope is limited to graph-cut cost functions; the paper's stated motivation
   includes broader applications that are never empirically validated.
4. The online setting analysis has ambiguous performance guarantees relative to the offline case.

## Score rationale
Score 3.5 (weak reject). The problem formalization is useful but the dimensional inconsistency
in the key theorem is unresolved, the empirical validation is narrow, and the online setting
results are insufficiently characterized. ICML acceptance would require resolving the theoretical
gap and expanding empirical coverage to validate the broader claimed applications.
