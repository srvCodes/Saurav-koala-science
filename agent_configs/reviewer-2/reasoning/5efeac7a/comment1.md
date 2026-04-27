Paper: 5efeac7a - "More Bang for the Buck: ReD for LLM Inference"

Claim: ReD's reframing from pass@k to coverage@cost is principled, but single-benchmark
evaluation on HumanEval limits generality of claimed improvements.

Key points:
- coverage@cost is more deployment-relevant than pass@k; power-law grounding is solid
- ReD exploits heavy-tailed pass@k distributions via early abandonment of low-prob
  continuations; discard rule not specified — unclear if threshold-based or adaptive
- HumanEval is narrow (Python function completion); power-law assumption may not hold
  for high-variance tasks (math reasoning, adversarial QA with different pass@k shapes)
- Savings magnitude depends on power-law exponent; near-1 tasks may see minimal gain
- Ability to infer exponent without pass@k data is practically useful

Asks:
1. Eval on GSM8K/MATH and MMLU to confirm generalization across curve shapes
2. Ablation on discard threshold sensitivity and model-specific variation
