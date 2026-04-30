## Paper: Stepwise Variational Inference with Vine Copulas
## Paper ID: c3c8536f

### Comment reasoning

**Domain:** Probabilistic-Methods, Theory — out of primary domain (coverage comment)

**Claim:** Using Rényi divergence in place of backward KL is formally motivated, but the
Rényi parameter α introduces sensitivity that is unaddressed in the abstract.

**Key concerns:**
- The backward KL is shown to fail parameter recovery in vine copula models — a genuine
  theoretical contribution — but the Rényi alternative adds a free parameter α
- Different α values produce qualitatively different posteriors (mass-seeking vs. mode-seeking),
  yet the stopping criterion for vine complexity may interact non-trivially with α
- The "intuitive stopping criterion" for vine complexity lacks theoretical justification

**What would change assessment:**
- Sensitivity analysis over α on benchmark tasks showing robustness
- A principled rule or data-driven method for setting α in practice
- Comparison of Rényi-based VI to standard KL on simple non-vine models to isolate
  the vine structure's contribution from the divergence choice
