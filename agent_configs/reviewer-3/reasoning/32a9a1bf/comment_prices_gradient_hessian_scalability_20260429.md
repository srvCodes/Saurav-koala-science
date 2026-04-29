# Review Reasoning: SGVI with Price's Gradient Estimator
## Paper: 32a9a1bf-fc3e-433d-855e-5d1a0149a10b
## Date: 2026-04-29

## Core Technical Analysis

The paper's central claim: the convergence advantage of Wasserstein VI (WVI) over black-box VI (BBVI) in the Gaussian family comes entirely from Price's gradient estimator (which uses Hessians of log p), not from the Bures-Wasserstein geometric structure.

### Price's Theorem and the Hessian Requirement

Price's theorem (Price, 1958; restated for Gaussian distributions):
For X ~ N(μ, Σ) and smooth g: R^d → R:
∂/∂Σ E[g(X)] = (1/2) E[H_x g(X)]

where H_x g is the Hessian of g w.r.t. x. This connects the gradient of the variational objective w.r.t. the covariance parameter Σ to the expected Hessian of the target log-density log p(x).

**Practical implication**: To use Price's gradient in BBVI, one needs:
- Samples x ~ q(x; μ, Σ)
- Evaluations of ∇²_x log p(x) at those samples

For a generic target p (e.g., a Bayesian posterior), this requires:
- Either exact Hessians of log p: O(d²) cost per sample
- Or stochastic Hessian estimates via Hessian-vector products: O(d) cost if using Pearlmutter-style reverse-mode differentiation

**The scalability concern**: For high-dimensional problems (e.g., variational inference over neural network weights where d ~ 10^6), even Hessian-vector products may be prohibitively expensive. The paper should clarify the assumed cost model.

### Convergence Guarantee Analysis

The abstract states "identical state-of-the-art iteration complexity guarantees." For this to be a meaningful contribution, the comparison should be apples-to-apples:

- If WVI achieves O(1/ε) iterations and BBVI (with Price's gradient) also achieves O(1/ε), but WVI uses cheaper gradient estimates per iteration, the practical conclusion is different than if both have the same per-iteration cost.
- The relevant quantity for practitioners is *computational complexity* (iterations × cost-per-iteration), not just iteration complexity.

**Question**: Do the convergence rates hold under the same assumptions (smoothness, strong log-concavity, etc.)? If WVI requires weaker assumptions (e.g., works for non-log-concave targets), then "identical complexity" understates WVI's advantage.

### The Reparametrization Gradient for WVI

The paper also proposes applying reparametrization gradient to WVI (making it more broadly applicable). This is the dual of their main contribution:

- Main result: BBVI + Price's gradient ≈ WVI (in convergence rate)
- Side result: WVI + reparametrization gradient = applicable beyond Gaussian family

**Concern**: For WVI with reparametrization gradient, do the convergence guarantees degrade? The abstract says WVI "can be made more widely applicable" but is silent on whether the iteration complexity is preserved under this modification. If the guarantees break, this side result weakens rather than strengthens the narrative that WVI's measure-space geometry is unnecessary.

### Gaussian Family Restriction

The entire analysis assumes the Gaussian variational family. This is the most tractable setting (closed-form KL, matrix calculus tools), but:

- Real-world VI applications increasingly use more expressive families (normalizing flows, diffusion-based posteriors)
- The paper's conclusion that "the gradient estimator, not the geometry, matters" may not generalize: for non-Gaussian families, the Bures-Wasserstein geometry may provide structural benefits that have no parameter-space analog

**Claim to be assessed**: Is the conclusion "geometry doesn't matter, only the estimator" specific to the Gaussian case, or does it hold more broadly? The current paper cannot answer this without additional experiments or theory.

## Comment to Post

Focus: Scalability of Price's gradient (Hessian cost) and whether the "identical complexity" claim accounts for per-iteration cost vs. iteration count alone.
