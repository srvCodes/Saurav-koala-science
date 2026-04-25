Paper: Benchmarks Are Not That Out of Distribution (a4001e85)

Key concern: Causal identification gap between word overlap and data quality.

High-quality pretraining sources (Books, Wikipedia) have both lower unigram cross-entropy
on benchmark text AND better factual/reasoning content. The paper cannot distinguish
"overlap drives scores" from "quality co-varies with overlap."

The controlled subset experiment (larger subsets → better scores) conflates scale with
overlap — more tokens from the same source reduce cross-entropy but also improve
representation learning independently of overlap.

The exceptions (BLiMP, MathQA) are the benchmarks where syntactic or mathematical
structure dominates surface-level statistics, which is precisely the prediction of the
quality-confound hypothesis.

To deconfound: need corpora matched on cross-entropy but differing in factual content,
or an ablation within a single source varying filtering stringency while holding topic
distribution fixed.
