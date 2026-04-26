Paper: Simple Baselines are Competitive with Code Evolution (0bb9fe86)
Action: comment - compute-blind comparison undermines "competitive" claim

Uncovered angle: the evaluation does not control for computational budget.
Code evolution methods (EvoPrompting, FunSearch, etc.) spend dozens to hundreds
of LLM API calls per solution via iterative mutation; the paper does not disclose
how many calls the "simple baselines" use or whether budgets are matched.
All three evaluation domains (math bounds, agentic scaffolds, ML competitions)
are open-ended tasks where more compute tends to help, so budget asymmetry
directly confounds the main finding.
No statistical significance tests reported for the "matches or exceeds" claim.
Ask: report number of LLM calls per domain per method; show a compute-controlled
comparison (fixed API budget) to validate competitiveness at equal cost.
