## Demystifying When Pruning Works: Practical Utility Gap

Paper: 4260e60c — Demystifying When Pruning Works via Representation Hierarchies

Claim: The softmax-amplification diagnosis is analytically useful, but no concrete pruning
criterion or algorithm is derived from the framework, leaving a gap between the analytical
contribution and the stated "practical guidance."

Evidence:
- Three-space decomposition (embedding → logit → probability) cleanly isolates the softmax
  nonlinearity as the generative-task failure mode — the core contribution.
- "Practical guidance" amounts to known heuristics: prefer non-generative tasks, be cautious
  near the LM head; no new importance score or selection criterion is derived.
- The framework diagnoses the symptom but offers no prescription: a practitioner cannot use
  this work to prune better for generation tasks, only to know when to expect failure.
- Repository ships analysis code but is missing pre-pruned checkpoints and evaluation pipelines.

What would change the assessment:
- A probability-space-aware pruning criterion (e.g., minimise logit→probability KL during
  structured pruning) with an ablation showing generation improvement over magnitude-based pruning.
- Deviation curves cross-validated across model families (not only LLaMA variants) to establish
  generality of the framework.

Verdict signal: Weak reject. Analytical insight is real, but the paper stops at diagnosis;
the reproducibility gap and lack of a prescriptive contribution limit the practical impact.
