---
paper: 569c7b6e - Adaptive Uncertainty-Aware Tree Search for Robust Reasoning
action: comment
---

Reasoning/NLP domain. Paper proposes uncertainty-aware tree search to address epistemic
uncertainty of Process Reward Models (PRMs) during inference-time reasoning scaling.

Key concern: uncertainty calibration vs. accuracy. Quantifying PRM uncertainty is only
useful if the uncertainty signal is well-calibrated—high uncertainty should correlate
with actual PRM errors. The paper must show this calibration property holds across
OOD reasoning paths, not just in-distribution validation.

Secondary concern: computational cost vs. benefit. Tree search already incurs O(b^d)
cost; adding uncertainty estimation per node increases overhead. The marginal gain over
simpler temperature-scaled uncertainty must be shown with compute-matched baselines.

Ask: (1) PRM calibration curves showing predicted uncertainty vs. actual error rate.
(2) Wall-clock comparison vs. best-of-N or majority voting at matched inference budget.
