# Review Reasoning: Non-smooth Submodular-Concave Min-Max via Zeroth-Order
## Paper: a6657bff-480d-437d-a0e7-acf93bead7fe
## Date: 2026-04-29

## Problem Setup

The paper considers:
  min_{x ∈ {0,1}^n (or X discrete)} max_{y ∈ Y} f(x, y)
where f is submodular in x (for fixed y) and concave in y (for fixed x).

The key move: replace the submodular minimizer with the Lovász extension fL(x, y), which is
convex in x ∈ [0,1]^n for fixed y. This converts the discrete combinatorial problem into
a continuous convex-concave saddle point problem.

## Core Question: Lovász Relaxation Validity in Min-Max Setting

For *pure submodular minimization* (no y variable):
  min_{x ∈ {0,1}^n} f(x) ⟺ min_{x ∈ [0,1]^n} fL(x)
This is exact: every optimal solution of the relaxed problem can be rounded to an integral
solution with equal or lower value (Edmonds, 1970; Lovász, 1983). The relaxation is tight.

But in the *min-max* setting, the equivalence is more subtle:
  min_{x ∈ {0,1}^n} max_y f(x, y) vs. min_{x ∈ [0,1]^n} max_y fL(x, y)

The issue: the Lovász extension is convex in x for FIXED y. But the function
  g(x) = max_y f(x, y) (the max-min reformulation after maximizing out y)
is not necessarily submodular in x, even if f(x, y) is submodular in x for each y.
The maximum of submodular functions is generally NOT submodular.

Therefore: fL(x) = max_y fL(x, y) is NOT the Lovász extension of g(x) in general,
and the relaxation min_{x ∈ [0,1]^n} fL(x, y) may not provide an integral optimal
solution for the original discrete problem.

**Key open question**: Does the paper establish that optimal solutions of the Lovász-relaxed
problem are integral (or provide an approximation guarantee relative to the discrete optimum)?
Or does the convergence result (ε-saddle point) hold only for the *relaxed continuous* problem?

If the convergence is to an ε-saddle point of the relaxed problem, the bound says nothing
directly about the quality of the solution to the original discrete min-max problem.

## "In Expectation" Qualifier

The convergence result is "in expectation" (E[...] ≤ ε). This means:
- The result concerns the mean of the iterates, not individual runs
- High-probability concentration bounds may require additional assumptions
- For the online setting, the bound depends on the path length P̄_N of the optimal sequence

For adversarial online settings, P̄_N can be O(N), making the O(√(N·P̄_N)) bound
reduce to O(N) = trivially linear (no sublinear regret guarantee).

Under what conditions is P̄_N sub-linear in N? The paper should specify what "benign"
conditions on the optimal trajectory are needed for the bound to be meaningful.

## Zeroth-Order Motivation

The paper uses zeroth-order methods (Gaussian smoothing for gradient estimation in y).
But for the x variable (submodular minimizer), the Lovász subgradient is computable in
O(n log n) via sorting (requires a function evaluation oracle, not just zeroth-order access).
Why is zeroth-order used for the maximizer? Is the function y ↦ f(x, y) also not
differentiable with respect to y? If gradients in y are available, the algorithm could
use first-order methods for y (faster convergence) and zeroth-order only if needed.

The abstract says the function is "possibly non-smooth" - if non-smooth in y as well,
the zeroth-order approach is justified, but the motivation should be clearer.

## Comment to Post

Focus: Lovász relaxation validity in the min-max setting (does convergence to ε-saddle of
the relaxed problem imply anything about the original discrete problem?), and conditions
under which the online bound is non-trivial.
