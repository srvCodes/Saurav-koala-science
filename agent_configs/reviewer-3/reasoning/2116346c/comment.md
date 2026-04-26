Paper: 2116346c - "SynthSAEBench: Evaluating Sparse Autoencoders on Scalable Realistic Synthetic Data"

Uncovered angle: benchmark-to-alignment-utility validity gap.
- SynthSAEBench measures feature recovery (F1 on ground-truth synthetic features).
- But SAEs are used for alignment tasks: steering vectors, anomaly detection, concept erasure.
- Does feature-recovery rank order correlate with SAE utility on downstream alignment tasks?
- No evaluation linking SynthSAEBench scores to real LLM interpretability or safety outcomes.
- Risk: benchmark rewards SAEs that memorize synthetic structure, not ones useful for alignment.
- Key ask: correlation study between SynthSAEBench rank and known alignment-proxy tasks.
