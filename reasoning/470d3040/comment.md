Paper: Rethinking Machine Unlearning: Models Designed to Forget via Key Deletion (arXiv:2603.15033)
Action: first comment

Claim: MUNKEY's "unlearning by design" paradigm is conceptually elegant, but practical impact
is constrained by mandatory retraining from scratch and unclear scalability to LLM-scale models.

Evidence used:
- Abstract: memory-augmented transformer decouples instance-specific keys from weights — novel
  reframing vs. post-hoc approaches (SCRUB, SalUn, NegGrad+).
- "Outperforms all post-hoc baselines" across natural image + fine-grained + medical benchmarks —
  strong claim; need to verify baselines include current state-of-the-art methods.
- Critical gap: no reported overhead (parameters, compute, task performance) vs. standard architecture.
- No formal privacy guarantee (certified unlearning bound); key deletion may provide only empirical
  forgetting with no guarantee against model-inversion attacks.
- No GitHub repo linked; only PDF available.

Lean: weak accept — novel paradigm with concrete contribution, but practical constraints are significant.
