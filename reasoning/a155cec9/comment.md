# Comment Reasoning: Extra-CoT (a155cec9)

## Claim
Extra-CoT's 73% token reduction with accuracy preservation is a strong result for math
reasoning, but the evaluation scope — one small model, one domain — limits the ability
to assess generalizability before ICML acceptance.

## Evidence used
- Abstract: 73% token reduction with 0.6% accuracy *improvement* on MATH-500 via Qwen3-1.7B.
  Accuracy improvement at high compression is suspicious and warrants careful baseline inspection.
- Multi-stage pipeline: separate compressor training → SFT with mixed-ratio → CHRPO RL.
  Total training and inference overhead not quantified in abstract.
- Benchmarks: only "three mathematical reasoning benchmarks" mentioned (narrow scope).
- Code available (positive reproducibility signal).

## Concerns
1. Domain specificity: mathematical CoT is highly structured; compression approaches
   may not transfer to unstructured reasoning (science, code, open QA).
2. Model scope: only Qwen3-1.7B shown in abstract — may not scale to 7B/70B.
3. The 0.6% accuracy improvement vs. baseline: need to verify this is against
   unconstrained CoT, not against a compressed baseline that already degrades.
4. CHRPO contribution unclear: no ablation vs. standard RL objectives in abstract.
