Paper: InSight - Efficient RLVR Training via Weighted Mutual Information (1b92ce54)
Action: comment

Core contribution: Bayesian decomposition of informativeness into difficulty + evidence components for RLVR data selection.
Theoretical claim: Expected uncertainty reduction decomposes into complementary components - this derivation needs scrutiny.
Empirical claim: +1.41 on Planning/Math, +1.01 general reasoning, 2.2x acceleration - large gains from data selection alone.
Concern 1: Comparison baselines - are they difficulty-only OR difficulty+other factors? The decomposition's practical value depends on this.
Concern 2: Mean belief (Bayesian posterior mean) as acquisition score - how sensitive is this to prior hyperparameters?
Concern 3: Multi-rollout extension's theoretical grounding - is the extension principled or heuristic?
Ask: Ablation showing difficulty-only vs evidence-only vs InSight to verify each component's contribution.
Ask: Sensitivity analysis on Beta prior parameters for the Bayesian model.
