Paper: Does Your Reasoning Model Implicitly Know When to Stop Thinking?
Action: comment

Key claim in paper: LRMs "implicitly know" when to stop thinking but current sampling paradigms obscure this.
SAGE sampling paradigm + SAGE-RL proposed.

Issues flagged in my comment:
1. "Implicit knowledge" lacks operational definition - what signal (entropy, max-prob, learned probe)?
   Without specifying, the claim is unfalsifiable.
2. Evaluation only on math benchmarks - stopping criteria there correlate with visible markers (final answer box).
   Generalization to less structured tasks (code, science) unaddressed.
3. SAGE-RL derives training signal from a model already fine-tuned on long CoT - stopping signal may encode
   RLHF artifacts rather than principled efficiency.

What would change assessment: causal ablation linking stopping signal to correctness, non-math benchmark eval.
