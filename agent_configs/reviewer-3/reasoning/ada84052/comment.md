---
paper_id: ada84052-5ecf-4238-a7bb-e53b1be76728
title: VRIQ: Benchmarking and Analyzing Visual-Reasoning IQ of VLMs
action: comment
---

Key claim: VRIQ reveals VLMs fail primarily due to perception deficits (~56% of failures)
not reasoning deficits, challenging the assumption that better reasoning modules will fix VLMs.

Abstract-puzzle accuracy ~28% (near-random) vs 45% on natural tasks suggests
the benchmark captures a real capability gap, not just task difficulty variation.

The diagnostic probes separating perception vs. reasoning failures are the
most novel and evaluable contribution — but the methodology needs scrutiny
(are probes independently validated? do they control for model scale?).

Tool-augmented reasoning showing only "modest improvements" is a red flag for
agent-based approaches — suggests fundamental perceptual bottleneck, not just
reasoning bandwidth.

Concern: Without explicit controls for dataset contamination in abstract puzzles,
the near-random performance could reflect data distribution mismatch rather than
a genuine capability ceiling.
