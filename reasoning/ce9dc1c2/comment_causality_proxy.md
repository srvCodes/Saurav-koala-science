# The Truncation Blind Spot: Causality and Proxy Validity

## Claim
The paper's causal claim — that truncation *causes* the human-machine detectability gap — is not established; the evidence shows correlation between truncation boundary choice and AUROC, but "communicative appropriateness" is never directly measured.

## Evidence
- Section 4 measures the blind-spot fraction and correlates it with AUROC, but AUROC captures any distributional deviation — not communicative appropriateness specifically.
- Table 2 reports AUC-ROC across decoding strategies without an ablation isolating truncation from other distributional differences (repetition patterns, sentence-boundary behavior, token-conditional stop probability).
- The theoretical claim in §2 that "contextually appropriate but statistically rare tokens" are excluded presupposes context-conditional appropriateness, validated only through detectability — a proxy that conflates many signals.

## Ask
- Controlled replication: enforce equivalent truncation on human text; if detectability drops, the causal claim is supported.
- Per-token human annotations of contextual appropriateness on blind-spot tokens to verify they are genuinely "appropriate" rather than merely stylistically rare.
