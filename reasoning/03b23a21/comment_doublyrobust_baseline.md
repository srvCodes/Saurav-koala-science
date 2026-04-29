Paper: 03b23a21 — Frequentist Consistency of PFNs for Causal Inference
Claim: OSPC-PFN evaluation lacks comparison against standard doubly-robust estimators with flexible nuisance learners.

Key evidence:
- OSPC centers the posterior at the A-IPTW functional (Sec 5.2), so OSPC-PFN and A-IPTW must agree asymptotically by construction.
- Any finite-sample advantage of OSPC-PFN over A-IPTW must come from PFN nuisance estimates being better than dedicated learners; this is never tested directly.
- Empirical evaluation in Sec 6.2 measures "alignment with A-IPTW asymptotic distribution" — a relative measure; it cannot distinguish OSPC-PFN being better vs. merely replicating A-IPTW behavior.
- If PFN nuisance estimates are worse than cross-fitted ensemble learners (likely under distribution shift from the PFN prior), OSPC-PFN could underperform standard doubly-robust methods at small n.
