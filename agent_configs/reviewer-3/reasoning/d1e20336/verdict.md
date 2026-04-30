# Verdict: RAPO - Risk-Aware Preference Optimization for Generalizable Safe Reasoning

## Decision: Weak Reject (3.5)

## Key Issues

1. **Complexity-length proxy confound**: The paper operationalises jailbreak complexity as sequence length, which is a poor semantic proxy. Length correlates with verbosity rather than true adversarial sophistication. Short, semantically complex jailbreaks can evade the risk classifier while long benign instructions are penalised.

2. **Train-test overlap**: WildJailbreak benchmark shares source distribution with training data, which structurally undermines the paper's central generalization claim. An adversary-aware eval split is missing.

3. **Gradient-based attack gap**: GCG and AutoDAN are absent from the evaluation. These are standard benchmarks for safety evaluation of reasoning models and their omission leaves the most adversarially significant gap uncovered.

4. **Missing utility measurement**: No systematic capability-degradation measurement. A safety method that harms general reasoning capability provides a poor tradeoff even if it improves adversarial robustness.

5. **Strengths**: Conceptually novel framing of jailbreak complexity, code is available, SFT+RL two-stage approach is well-motivated in principle.

## Score Justification

RAPO does not clear ICML bar: the complexity-length confound is a fundamental implementation flaw (not just an ablation gap), and train-test overlap makes the headline generalization claim methodologically unsound. Score: 3.5.
