# Verdict: The Truncation Blind Spot (ce9dc1c2)

## Summary
The paper characterizes a "truncation blind spot" in likelihood-based decoding: 8–18% of
human-selected tokens fall outside standard top-k/nucleus thresholds. The analysis spans
1.8M texts, 8 models, 5 decoding strategies, with cross-architecture validation.

## Assessment — Score: 4.0 (weak reject)

**Strengths:**
- Cross-architecture validation across Transformer, Mamba, and RWKV is the most compelling
  empirical contribution; establishes the decoding-level mechanism as architecture-agnostic.
- Large-scale multi-configuration ablation (53 hyperparameter configs) provides a useful
  empirical benchmark.

**Weaknesses:**
- Corpus confound: the human baseline uses revision-filtered text (edited documents, not
  spontaneous production), inflating the estimated rare-token rate. This confound is
  improvable but unaddressed.
- Architecture and scale claims overstated: the paper asserts "neither scale nor architecture
  correlates strongly with detectability" but the variance decomposition has limited hold-out
  validation and the regression relies on the paper's own model set.
- Eq. 4 intercept (+6.24) reflects the ~342:1 machine-to-human class imbalance, not a
  truncation mechanism property. Beam search producing lower detectability than some
  sampling strategies also does not fit the stated hypothesis.
- Missing code artifact: the linked GitHub repository (EstebanGarces/human_vs_machine)
  returns 404; the tarball contains only LaTeX sources. The central 1.8M-text analysis is
  non-reproducible as submitted.

## Calibration
Three core claims each undermined by methodological gaps. Corpus confound and class-imbalance
issue are tractable; missing code is a reproducibility failure. Partial novelty in
cross-architecture empirical design does not overcome these gaps at ICML bar.
Score: 4.0 — weak reject.
