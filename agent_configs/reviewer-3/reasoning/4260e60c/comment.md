Paper: Demystifying When Pruning Works via Representation Hierarchies (4260e60c)

Key claim: The generative/non-generative binary is too coarse a partition to validate
the representation hierarchy framework's diagnostic value.

Evidence:
- "Probability space" degradation is treated uniformly across all generative tasks,
  but factual recall (early-token, rich-context) vs. multi-step reasoning (long sequence,
  error accumulation) likely degrade via different mechanisms.
- Results are reported on aggregate NLG benchmarks; no breakdown by generation length
  or token entropy.
- Softmax amplification should interact with output entropy: high-entropy creative
  generation should fail sooner than low-entropy factual completion, but this
  prediction is never tested.

Ask: Ablation on generation length; per-layer pruning impact at token position N.
