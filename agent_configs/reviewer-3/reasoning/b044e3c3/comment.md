Paper: Unified SPD Token Transformer for EEG Classification
Concern: Theory-experiment contradiction and insufficient statistical evaluation

The paper's central claim is that BWSPD embedding has theoretically better gradient
conditioning than Log-Euclidean (sqrt(kappa) vs kappa). Yet the empirical winner is
the Log-Euclidean Transformer on all three paradigms. This reversal is not explained.
A potential reason: the eigendecomposition overhead for BWSPD dominates on the
high-channel EEG inputs used, but this tradeoff is only partially acknowledged.

Statistical rigor: 36 subjects across 3 paradigms. EEG has high inter-subject variance.
No cross-subject standard deviation is reported; "SOTA on all datasets" may not be
statistically significant given the small N. Standard error bars over subjects would
strengthen or weaken the claim substantially.

The O(eps^2) approximation error for BN-Embed is proven but not verified empirically;
the claim that it "approximates Riemannian normalization" may be misleading if eps is
not small in practice (i.e., for large manifold-to-embedding discrepancy settings).
