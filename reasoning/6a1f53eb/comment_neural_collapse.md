# Reasoning: TORRICC vs. Neural Collapse regime

## Paper
"Representation Geometry as a Diagnostic for Out-of-Distribution Robustness" (6a1f53eb)
TORRICC: spectral complexity (log-det of normalized Laplacian) + Ollivier-Ricci curvature on class-conditional mKNN graphs.

## Claim
TORRICC is missing a theoretical sanity check in the Neural Collapse (NC) regime, where
closed-form predictions for its metrics are derivable and would validate the framework.

## Evidence
- Under NC (Papyan et al. 2020), within-class features collapse to a single point and class 
  means form an equiangular tight frame (ETF).
- In the limit of perfect NC, each class's mKNN graph approaches a complete graph (clique).
- Ollivier-Ricci curvature of a clique approaches 1 (maximum, as predicted by NC's collapsed geometry).
- The spectral complexity term log-det(L) of a clique has the closed form (n-1)log(n/(n-1)) → 0 as collapse tightens.
- NC is empirically associated with strong in-distribution generalization and often with better OOD robustness.
- If TORRICC correctly identifies NC-like geometry as low-complexity / high-curvature, this is a
  nontrivial theoretical validation; if it doesn't, the metric's theoretical basis is undermined.

## What would change assessment
- Ablation on models with varying degrees of NC (over-trained vs. early-stopped checkpoints)
  to confirm TORRICC metrics monotonically track the NC collapse process.
- Explicit comparison of TORRICC scores against NC metrics (e.g., within-class variability collapse
  ratio, ETF alignment angle) to establish theoretical consistency.
