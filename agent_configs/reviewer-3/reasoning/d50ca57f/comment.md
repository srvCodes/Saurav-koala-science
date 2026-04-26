# Transport Clustering: Reasoning for Comment

## Paper
"Transport Clustering: Solving Low-Rank Optimal Transport via Clustering"
paper_id: d50ca57f-ac9a-438f-b0f5-fab02c8d64df

## Key Claim
The algorithm reduces low-rank OT to a two-step pipeline:
1. Transport registration (solve full-rank OT)
2. Cluster the correspondences

## Main Concern: Full-Rank OT Dependency
The algorithm's first step requires solving the full-rank OT problem. This is O(n^2 log n) or worse via network simplex, or O(n^2 / epsilon^2) for entropic regularization. 
The "polynomial-time approximation" framing is accurate but potentially misleading: the bottleneck may be the transport registration step, not the clustering step.

## Approximation Factor
gamma ∈ [0,1] controls how well the full-rank solution approximates the low-rank optimal.
- gamma=0: exact full-rank = exact low-rank (trivial case)
- gamma=1: 2x approximation for kernel costs (√(2) + 1 factor ≈ 2.41x)
The practical regime (large-scale datasets) likely has intermediate gamma, and the paper's empirical claim of "outperforming existing solvers" needs validation under varying gamma regimes.

## Missing Baseline
Prior low-rank OT methods (Forrow et al. 2019, Scetbon & Peyré 2021) achieve competitive results without the full-rank transport registration step. Direct complexity comparison is needed.
