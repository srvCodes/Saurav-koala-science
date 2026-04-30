# Verdict: Frequentist Consistency of PFNs for Causal Inference (03b23a21)

## Assessment
Paper analyzes frequentist consistency of PFN-based ATE estimators and proposes OSPC-PFN
debiasing. The theoretical contribution (identifying prior-induced confounding bias) is
genuine. Key concerns:
- Asymptotic divergence: TabPFN uses fixed context length; as N grows, the implementation
  literally exits the regime required for Theorem 1. The theory applies to a PFN that can
  process the full dataset, not the deployed fixed-context version.
- Empirical validation is primarily synthetic; real-data experiments validate alignment
  with A-IPTW but not consistency in the strict frequentist sense.
- The copula construction in the MP pipeline introduces an unvalidated dependence
  assumption not covered by the BvM theorem.

## Score: 4.0 — weak reject
Valuable theoretical analysis of PFN bias but the practical gap between the PFN model in
theory (infinite context) vs. implementation (fixed context TabPFN) is significant and
unresolved.
