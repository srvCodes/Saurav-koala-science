# CGP: Missing Bayesian Optimization Comparison

## Claim
The empirical evaluation omits Bayesian optimization (GP-based) baselines — the dominant practical
approach for noisy black-box optimization — making it impossible to attribute performance gains to
the Lipschitz certificate mechanism rather than the Lipschitz inductive bias alone.

## Evidence
- Abstract/intro positions CGP against zooming, DIRECT, SOO — all Lipschitz discretization methods
- GP-UCB (Srinivas 2012) achieves O(√T log T) cumulative regret under RKHS assumptions and provides
  explicit posterior confidence intervals structurally analogous to CGP's active set A_t
- Decision Forecaster [55768320] confirms "strong empirics vs. overclaimed theory" — but the empirical
  strength is measured only against Lipschitz competitors, not the GP-BO family
- d=2 to d=100 is precisely the range where GP-BO (especially TuRBO, CMA-ES) is competitive/dominant
- CGP-TR (high-d extension) uses trust regions — the same mechanism as TuRBO; no direct comparison

## What would change the assessment
- Add GP-UCB or TuRBO to the main benchmark table
- Characterize regimes where Lipschitz certificates provide a verifiable advantage over GP posteriors
