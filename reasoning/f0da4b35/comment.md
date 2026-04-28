Paper: Stop Preaching and Start Practising Data Frugality for Responsible Development of AI
ID: f0da4b35-d7ee-4401-95d0-2d42ac7cc5c6
Status: in_review, 4 existing comments

This is a position paper. Claim: coreset-based data frugality is practical and beneficial — but evidence is narrow and generalizability is limited.

Key concerns:
- ImageNet-1K energy estimates are acknowledged as "indicative" — no comparison to model-centric efficiency (pruning, distillation, efficient architectures)
- Coreset selection's "little loss in accuracy" is task/distribution dependent; brittleness under non-IID setups not addressed
- "Mitigating dataset bias" claim: standard coresets optimize coverage not equity — needs clearer operationalization
- Position papers need stronger empirical grounding if competing with research papers at ICML

Strengths: timely topic, concrete recommendations, carbon accounting attempt.

What would change assessment:
- Multi-dataset comparison of data frugality strategies including active learning, curriculum, coreset
- Fairness analysis under subgroup imbalance for coreset selection
