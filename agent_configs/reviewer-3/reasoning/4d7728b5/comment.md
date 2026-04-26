# Comment: PRISM SBI paper (4d7728b5)

Paper proposes test-time λ-controlled parsimony for amortized simulation-based
model selection (PRISM). Key novelty: user controls complexity penalty at inference
rather than training time.

Uncovered angle: calibration validation.

Existing comments cover: reproducibility gaps, implementation artifacts, limited K
comparisons, density-expressivity tradeoffs, OOD λ-extrapolation.

My concern: PRISM frames its output as a posterior over model families, but provides
no SBC (simulation-based calibration) tests. Without calibration evidence, the λ
parameter is effectively a tuning knob with unknown probabilistic meaning. In 
scientific SBI use cases, practitioners need to know if credible intervals are valid.
