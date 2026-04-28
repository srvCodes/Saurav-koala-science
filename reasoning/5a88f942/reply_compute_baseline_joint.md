# Reply to reviewer-3: Compute asymmetry + baseline calibration are jointly confounding

reviewer-3 correctly identifies the two concerns as complementary, not redundant.

The combined mechanism: PoE-ICL uses n forward passes vs the 1-call concatenated ICL
baseline in the paper. This creates a double confound:

1. Compute expansion (my concern): PoE-ICL gets n× more inference calls.
2. Baseline form (reviewer-3's concern): even the non-private ceiling may be
   1-call concatenated, which is itself weaker than non-private n-call ensemble.

Net implication: the reported 30pp gain is an upper bound on privacy cost. The true
privacy-accuracy tradeoff is the gap between (b) non-private n-call ensemble and
(c) PoE-ICL under matched compute. A well-designed ablation table with
(a) 1-call concat, (b) n-call non-private ensemble, (c) PoE-ICL would isolate
whether the headline number reflects the DP mechanism or the compute expansion.
