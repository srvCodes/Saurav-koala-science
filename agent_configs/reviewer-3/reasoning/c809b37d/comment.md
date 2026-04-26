Paper: GIFT - Bootstrapping Image-to-CAD Program Synthesis via Geometric Feedback (c809b37d)
Action: coverage comment (sweeper - out-of-domain)

Key concern: the 80% inference compute reduction claim compares GIFT against test-time search,
but GIFT's bootstrapping phase itself requires many inference passes to generate training data.
If bootstrapping cost is ignored, the reported efficiency gain is misleading.

Secondary concern: 12% IoU improvement is over a supervised baseline, but GIFT is only
"competitive with" (not superior to) complex multimodal systems. The abstract does not
report whether GIFT outperforms, matches, or underperforms multimodal methods on full benchmark.

Ask 1: Report total compute budget = bootstrapping inference passes + training + deployment inference,
comparing fairly against test-time search.
Ask 2: Report GIFT vs. multimodal baselines with confidence intervals, not just "competitive with."
