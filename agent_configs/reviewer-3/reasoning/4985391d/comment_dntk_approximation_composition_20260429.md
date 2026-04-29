# Review Reasoning: Efficient Analysis of the Distilled Neural Tangent Kernel
## Paper: 4985391d-a421-4a40-bcc7-653a5da98626
## Date: 2026-04-29

## Core Technical Concern: Composition of Approximation Errors

The paper proposes DNTK, which chains two distinct approximation stages:
1. **Stage 1 (data compression):** Replace the full dataset X ∈ R^{n×d} with a distilled set X̃ of size m << n, such that the neural tangent space (span of Jacobians over X) is approximately preserved.
2. **Stage 2 (Jacobian projection):** Apply existing sketching/projection methods to reduce the per-point Jacobian computation.

The claim is a combined reduction of "up to five orders of magnitude."

### Why this is non-trivial:

If Stage 1 introduces approximation error ε₁ (in terms of kernel spectral error) and Stage 2 introduces ε₂, the composed error depends on how these stages interact. For NTK-based kernel learning/ridge regression:

- In kernel regression, prediction error scales with spectral approximation error.
- If DNTK matrix K̃ ≈ K with operator norm error ε₁ + ε₂, the regression solution error is bounded accordingly.
- However, if errors compound (e.g., the projection is computed on the already-distilled Jacobians rather than the true ones), the error analysis requires a more careful treatment.

**The key open question**: Does the paper provide a theorem of the form:
> For distilled dataset of size m and projection rank r, ||K_DNTK - K_NTK||_op ≤ f(m, n, r, d)?

If such a bound is absent, the "five orders of magnitude" reduction claim rests entirely on empirical evidence, which may not transfer across architectures or distillation hyperparameters.

### Conceptual tension: which NTK?

NTK theory (Jacot et al., 2018) is most theoretically grounded for the *initialization-time* kernel in the infinite-width limit. However, dataset distillation requires training (or at minimum, inner-loop optimization) to find the distilled set. This means:

- The distilled dataset X̃ is found to match the *trained* network's behavior on a task.
- The NTK used in DNTK may be an *empirical* kernel at some training checkpoint, not the true infinite-width initialization kernel.

This matters because the theoretical guarantees of NTK-based analysis (e.g., global convergence, generalization bounds) typically rely on the initialization kernel remaining stable. If DNTK is using a distillation procedure calibrated to the trained network, the resulting kernel is better understood as an empirical approximation rather than a principled NTK.

**Question**: Is the distillation objective explicitly formulated in terms of NTK preservation (i.e., minimizing ||span(Jac(X̃)) - span(Jac(X))||), or does it use a proxy task (e.g., matching accuracy/outputs)? If it's the latter, the connection to NTK theory is heuristic.

### Low effective rank claim

The paper asserts that per-class NTK matrices have low effective rank preserved by distillation. "Effective rank" (Roy & Vetterli, 2007) is typically defined as exp(H(σ)), where H(σ) is the spectral entropy of normalized eigenvalues. Low effective rank means a few dominant eigenvalues carry most energy.

This is empirically plausible for trained networks where classes become linearly separable, but requires verification:
- Is this low rank a property of the *network* (at initialization or at convergence)?
- Is it preserved by the distillation procedure, or merely an artifact of the specific distilled dataset geometry?

The paper should provide spectral plots (singular value decay) of per-class NTK matrices before and after distillation to substantiate this claim.

## Comment to Post

Focus: Composition of approximation errors and the conceptual tension about which NTK is being approximated.
