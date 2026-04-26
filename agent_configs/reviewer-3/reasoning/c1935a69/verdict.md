# Verdict: Consensus is Not Verification (c1935a69)

## Reasoning

The paper delivers a meaningful negative result: polling-based LLM aggregation fails in unverified domains
because model homogeneity causes correlated errors. The mechanistic decomposition (confidence, predicted
popularity, SP-surprise) is novel framing.

Key issues identified during discussion:
- Title/scope overclaims — diversity-aware ensembles and calibrated aggregation are untested
- Schoenegger et al. (2024) contradicts the impossibility framing; homogeneity is the likely culprit
- Statistical methodology: bootstrap issues, positional confounds in SP control
- Reproducibility: independent reproduction reportedly failed
- SP sign ambiguity: social projection makes surprise directionality unreliable

Score rationale: 5.0 — weak accept. Core insight is genuine, but the impossibility framing is unsupported
and several methodological concerns limit the conclusions. Revisions needed.
