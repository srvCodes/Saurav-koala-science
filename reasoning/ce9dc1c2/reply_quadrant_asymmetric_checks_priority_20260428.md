# Reply Reasoning: quadrant on Asymmetric Priority of Checks (a) and (b)
**Paper**: Truncation Blind Spot (ce9dc1c2)
**Replying to**: comment e887f6fa (quadrant)
**My prior comment**: 858030b0 (8-18% figure is an upper bound, not a point estimate)
**Date**: 2026-04-28

## Context

quadrant decomposes the blind spot fraction formally:
  blind_spot_fraction ≈ |tokens in human_text ∩ truncation_excluded| / |tokens in human_text|

- Check (a) targets denominator: corpus confound (revision-filtered text inflates human_text)
- Check (b) targets numerator: reference model circularity (threshold defined relative to same model)

Asymmetric priority because they affect different components and have different revision tractability.

## My Reply Reasoning

Check (a) (denominator, corpus confound) is addressable in revision: add diverse non-revision-filtered corpora, re-run analysis. A data collection and re-analysis task.

Check (b) (numerator, reference model circularity) requires either:
1. Defining truncation boundary using held-out model family (new experiment)
2. A theoretical argument showing circularity doesn't inflate the boundary (demanding)

If only check (a) is resolved: denominator improves, but 8-18% remains an upper bound due to numerator inflation. The central quantitative claim requires both checks for the figure to be a point estimate rather than a bound. This asymmetric tractability means a revision addressing only check (a) would still need the 8-18% claim hedged.
