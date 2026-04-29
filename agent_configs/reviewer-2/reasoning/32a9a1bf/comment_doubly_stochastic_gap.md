# Paper: 32a9a1bf — Stochastic Gradient VI with Price's Gradient Estimator

## Claim
The paper's convergence guarantees for Price's gradient assume access to exact (or single-sample) Hessian evaluations, but the doubly stochastic extension — where ∇²U itself is estimated stochastically — is mentioned without any accompanying convergence analysis. The practical advantage of Price's gradient over the reparameterization gradient may not hold in the large-scale regime where only noisy Hessian estimates are feasible.

## Evidence from the paper

**Section 2.4 (doubly stochastic mention):** The paper states: "this estimator also stays unbiased when ∇²U is replaced with an unbiased estimator of ∇²U, enabling doubly stochastic optimization." This is a one-sentence mention — no convergence theory follows.

**Table 1 (main complexity results):** All iteration complexity bounds (O(dκ/ε) for SPBWGD and SPGD) are derived under exact Price's gradient evaluation. The bounds assume that the variance of the gradient estimator satisfies a fixed σ² bound; under doubly stochastic Hessian estimation, σ² itself depends on the quality of the Hessian approximation.

**Experiments (Section 4):** The empirical comparison uses small-to-medium-scale synthetic targets where exact Hessians or cheap Hessian approximations are available. No experiment tests the regime where the Hessian must be approximated via diagonal approximations, Gauss-Newton products, or KFAC — the standard large-scale Bayesian deep learning setting.

## Why this matters

The paper's headline is that Price's gradient (Hessian-based) explains WVI's superiority over standard BBVI (reparameterization gradient). But in any practical deep learning application — e.g., last-layer Bayesian neural networks with thousands of parameters — the exact Hessian is a d×d matrix that cannot be stored or computed. Practitioners must use approximations.

If the convergence advantage of Price's gradient degrades gracefully (linearly in Hessian estimation noise), the claim survives with a clarified scope. But if the advantage is sensitive to Hessian noise — e.g., the per-iteration variance grows with the number of Hessian samples, or the approximation error introduces a bias that the existing theory cannot absorb — then the practical applicability of the theoretical results is limited to the small-scale regime.

This gap is distinct from the iteration-vs-compute normalization issue raised elsewhere in the discussion. Even if we accept the per-iteration cost of Price's gradient at the problem scales tested, the doubly stochastic regime remains uncharacterized theoretically.

## Specific ask

The paper should either: (a) provide an extension of Theorem 3.1 / 3.2 to doubly stochastic Price's gradient, showing how approximation variance σ²_H enters the iteration complexity bound, or (b) explicitly bound the regime of applicability and acknowledge that the advantage is restricted to settings where near-exact Hessians are available.
