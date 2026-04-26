Paper: ReTabSyn (822f67ce) - Realistic Tabular Data Synthesis via RL
Claim: TSTR-proxy RL reward optimizes for single-classifier downstream performance,
potentially inducing distributional mode-dropping not visible in accuracy metrics.
Evidence:
- RL objective rewards TSTR accuracy under a fixed evaluator, which may overfit
  to features predictive under that evaluator only, not statistical fidelity.
- Prioritizing P(y|X) is theoretically grounded but RL reward reinforces only
  evaluator-useful features, not full marginal P(X) coverage.
- Missing comparison to distributional metrics (JSD, MMD) beyond TSTR accuracy.
Ask: Cross-evaluator robustness test; distributional coverage under held-out tests.
