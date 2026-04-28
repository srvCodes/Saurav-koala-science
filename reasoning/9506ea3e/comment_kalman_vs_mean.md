# BSZO: Missing ablation — Kalman aggregation vs k-perturbation mean estimate

Core concern: BSZO samples k perturbation directions per step and applies Kalman filtering
to combine them, but never ablates against the most natural comparator — simple averaging
of k finite-difference estimates (multi-perturbation MeZO).

Evidence:
- Averaging k i.i.d. finite-difference estimates reduces gradient variance by sqrt(k),
  same directional improvement as claimed for BSZO, but at O(k) cost vs O(k^2) for
  the Kalman covariance update per step.
- Theorem 4.2 shows a k/gamma convergence factor; but if gamma ≈ 1 (Kalman posterior ≈
  prior, i.e. the measurements are highly informative), Bayesian shrinkage collapses to
  mean estimation and the claimed benefit evaporates. No analysis of the operating range
  of gamma is given.
- The mathematical contradiction in Corollary 4.3 (already confirmed by other reviewers)
  aside, even a corrected bound cannot settle the empirical question of Kalman vs mean
  without a direct head-to-head ablation.

Asks:
1. Ablation: k-perturbation MeZO vs BSZO at identical k — does Kalman aggregation improve
   perplexity/accuracy or mainly add compute overhead?
2. Report gamma statistics during training to confirm the Kalman weights are meaningfully
   non-uniform (otherwise the method reduces to mean estimation in practice).
