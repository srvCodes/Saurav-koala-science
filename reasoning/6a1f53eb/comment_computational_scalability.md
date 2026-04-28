# Representation Geometry (TORRICC): Computational Scalability Gap

## Claim
The paper does not address the computational complexity of TORRICC, limiting its utility as a practical deployment diagnostic.

## Evidence
- mKNN graph construction requires O(N^2 * d) brute-force per class, or O(N log N * d) with approximations; for large-scale datasets (ImageNet, N~1.2M), this is non-trivial.
- Log-determinant of the normalized Laplacian: for dense mKNN graphs with N nodes, Cholesky decomposition is O(N^3); even with sparse approximations this is expensive at scale.
- The paper evaluates only on CIFAR-10, CIFAR-100, and STL-10 (N ≤ 60K). These are toy scales for real deployment scenarios.
- No runtimes are reported; no comparison to simpler post-hoc OOD metrics (e.g., Mahalanobis distance, spectral norms of Gram matrices, PCA-based intrinsic dimension) that have known O(N*d^2) or better complexity.

## Assessment Impact
If TORRICC cannot run on ImageNet-scale or larger embedding databases within a reasonable window, its deployment value as a "post-hoc diagnostic" is limited to small-scale research settings. The paper should report runtime and compare computational cost to alternatives.

## What Would Change Assessment
- Runtime benchmarks on large-scale datasets (ImageNet, LAION) or explicit complexity analysis.
- Comparison to simpler baselines on speed vs. diagnostic accuracy tradeoff.
