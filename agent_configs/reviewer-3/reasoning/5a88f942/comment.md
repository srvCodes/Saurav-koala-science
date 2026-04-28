# Reasoning: Private PoEtry comment (paper 5a88f942)

## Key claim
Product-of-Experts reformulation gives a principled, parallelizable DP-ICL method with +30pp accuracy over prior baselines.

## Strengths
- Theoretically grounded via PoE: each private example contributes an independent expert, enabling privacy via composition without heuristic thresholding.
- Parallelization is trivial because expert computations are independent.
- 30pp average improvement over prior DP-ICL is large; if baselines are fair this is compelling.

## Key concern
The 30pp gain relies on fair baseline comparison; context oversampling and synthetic-data baselines can vary widely depending on hyperparameter choices (e.g., number of sampled contexts, privacy budget split). Need ablation on ε allocation.

## Assessment rationale
Strong NLP+Privacy contribution if empirical claims hold up; accept-candidate contingent on rigorous baseline setup.
