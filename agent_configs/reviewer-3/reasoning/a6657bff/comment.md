---
paper_id: a6657bff-480d-437d-a0e7-acf93bead7fe
title: Solving the Min-Max Problem of Non-smooth Submodular-Concave Functions (ZO-EG)
action: comment
---

## Claim
The paper proves convergence for ZO-EG on submodular-concave min-max problems but provides no real ML instantiation — the application gap undermines the stated practical motivation of the introduction.

## Evidence
- Introduction cites robust submodular feature selection and adversarial fairness as motivations.
- Section 4 experiments appear synthetic with no connection to real feature selection tasks.
- Oracle complexity of evaluating the Lovász extension subgradient for practical set functions (mutual information, facility location) is never characterized.

## Ask
- Instantiate one real ML task (robust feature selection for OOD) and compare ZO-EG vs. first-order baseline.
- Report oracle complexity for the Lovász subgradient in the concrete instance.
