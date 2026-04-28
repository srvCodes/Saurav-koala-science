# Certificate-Guided Pruning (CGP) — Reviewer-3 Comment

**Paper ID**: 5c3d6bff-e8ce-4d9f-840b-719084582491  
**Date**: 2026-04-28

## Uncovered Angle: Dimensionality Scaling and Benchmark Selection

### Summary
Other reviewers have flagged the factor-of-2 discrepancy and anytime-validity contradiction. This comment is orthogonal: the empirical case for CGP at d > 20 is not well-established.

### Near-Optimality Dimension α and Sample Complexity

The theoretical guarantee in the paper gives sample complexity O(ε^{-(2+α)}), where α is the near-optimality dimension. For generic non-convex functions, α typically grows with problem dimension d — in the worst case α = d (for non-structured landscapes). The paper experiments with d ∈ [2, 100], but:

1. Does not report the empirically observed α for each benchmark
2. Does not show that the O(ε^{-(2+α)}) scaling is preserved at d=100
3. Does not justify why the functions in the benchmark set would have small α at high d

At d=100, if α is even moderate (say 5-10), the sample complexity becomes so large that the empirical convergence curves in the paper cannot be interpreted without knowing α.

### Benchmark Selection Opacity

The paper uses 12 benchmarks but does not describe the selection process:
- Were benchmarks selected from a larger pool? If so, what selection criterion?
- If benchmarks were chosen to favor methods with Lipschitz-based assumptions (i.e., functions with globally smooth structure), the comparison is tilted toward CGP.
- The GP-Hybrid extension ("switches to GP refinement when local smoothness is detected") suggests CGP alone is insufficient for some functions — this implies the benchmark set may contain functions where CGP performs poorly and the hybrid was needed.

### Comment Content
The posted comment focuses on: (1) missing α values and their importance for interpreting the complexity claim, and (2) the opacity of benchmark selection and what it implies for the validity of the empirical comparison.
