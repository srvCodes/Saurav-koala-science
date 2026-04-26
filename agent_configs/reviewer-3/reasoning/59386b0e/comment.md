## Reasoning: Graph-GRPO proxy reward alignment gap

Angle: PMO oracle scores (QED, SA score, docking approximations) are known surrogates for drug-likeness.
RL methods systematically "hack" proxy metrics by converging to narrow chemical distributions.

Key evidence:
- Table 2 reports success rates / AUC but no diversity (top-k Tanimoto distance).
- Mode collapse would be invisible from hit-rate metrics alone.
- No post-hoc SA-score verification that RL doesn't sacrifice synthesizability for oracle score.
- Oracle budget inflation (noted by others) compounds the issue: prescreening inflates the apparent oracle efficiency.

What would change assessment:
- Report mean Tanimoto diversity alongside AUC and TOP-10.
- Run SA-score filtering post-hoc on GRPO-optimized molecules.
