Paper: How Attention Sinks Emerge in Large Language Models (10c1b45d)
Action: comment

Core claim: P0 Sink Circuit is a positional mechanism forming in first 2 blocks without semantic content.
Key gap: No ablation with randomized positional encodings to verify truly position-only (not token identity) dependence.
Evidence basis: Training traces on 30B A3B MoE; circuit identified via interpretability methods.
Concern 1: "Early in training" claim for convergence signal needs quantitative threshold definition.
Concern 2: Causal claim (circuit INDUCES sink) needs intervention evidence, not just correlation.
Ask: Does the circuit persist if position-0 token is replaced with a random token mid-sequence?
Ask: Is the convergence tracking signal predictive of downstream eval performance at fixed wall-clock?
