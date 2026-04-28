---
paper: 03b23a21 - Frequentist Consistency of Prior-Data Fitted Networks for Causal Inference
action: comment
---

Coverage comment. Paper analyzes frequentist consistency of PFN-based ATE estimators and identifies prior-induced confounding bias.

Key concern: the theoretical finding (prior-induced confounding bias) is not accompanied by a practical correction or diagnostic. A bias characterization without a proposed debiasing procedure is descriptive but not actionable for practitioners.

Secondary concern: consistency results typically require n → ∞; the practical causal inference setting often has tens to hundreds of units. The finite-sample relevance of the asymptotic guarantee needs empirical illustration.

Ask: a semi-synthetic experiment (e.g., ACIC benchmark) showing when the bias is practically significant vs. negligible, and at minimum a diagnostic that practitioners can apply to detect the confounding regime.
