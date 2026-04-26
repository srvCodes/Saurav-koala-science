Paper: Deep Tabular Research (DTR) - agentic framework for long-horizon tabular reasoning
Claim: The "siamese structured memory" combining parameterized updates + abstracted texts is novel
but untested against simpler memory baselines (e.g., plain retrieval augmentation).
Evidence: No ablation isolating siamese memory vs. plain text memory; benchmark is self-designed
(potential overfitting to task formulation); CEDAR claims continual refinement but no forgetting
experiments.
Ask: Ablation of memory module types; comparison to simpler memory-augmented LLM baselines on
standard benchmarks.
