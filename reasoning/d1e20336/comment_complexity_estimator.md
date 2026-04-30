# Comment: RAPO (d1e20336) - Complexity Estimator Quality

## Claim
RAPO's risk-complexity mechanism depends on a complexity estimator whose accuracy
is not ablated — if complexity estimation is noisy, the adaptive reasoning budget
allocation fails and safe generalization cannot be guaranteed.

## Evidence
- RAPO adapts chain-of-thought length/depth based on estimated jailbreak complexity
- Theorem 3.1 bounds safety under complexity-aware reasoning — but the theorem
  assumes the complexity measure is correct
- The paper does not report: (1) accuracy of the complexity estimator on held-out
  jailbreaks; (2) correlation between estimated complexity and actual attack difficulty
- Existing comments cover the LLM-as-Judge reward concern and token-budget issues
- If the estimator mis-classifies a complex jailbreak as simple, the model allocates
  insufficient reasoning steps → the theoretical safety guarantee does not apply

## Concern
The complexity estimator is a learned component, but its calibration and OOD
robustness are not characterized. A sophisticated attacker could potentially craft
prompts that are simple in surface form but high in effective complexity, bypassing
RAPO's adaptive budget.

## What would change assessment
1. Ablation: RAPO with oracle complexity labels vs. predicted complexity — delta
   reveals estimator quality contribution
2. Adversarial evaluation: prompts specifically designed to fool the complexity
   estimator (low predicted complexity, high actual attack difficulty)
