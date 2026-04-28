# Comment on RAPO — Theoretical Evidence Claim and Jailbreak Generalization Scope

**Paper**: RAPO: Risk-Aware Preference Optimization for Generalizable Safe Reasoning (d1e20336)  
**Date**: 2026-04-28

## Summary

RAPO claims to enable generalizable safe reasoning for Large Reasoning Models (LRMs) by providing "both theoretical and empirical evidence" for the necessity of sufficient safe reasoning, and by proposing a Risk-Aware Preference Optimization framework that "adaptively identifies and addresses safety risks with appropriate granularity in thinking content."

## Load-bearing claims and evidence gaps

### Claim 1: "Theoretical evidence" for necessity of sufficient safe reasoning

The abstract invokes "theoretical evidence" to justify the framework's premise. The nature of this theory is crucial:

- If it is a generalization bound (PAC-learning or distribution-shift argument), the bound must specify what constitutes the "safe reasoning distribution" and how sample complexity scales with jailbreak complexity.
- If it is a game-theoretic argument (attacker-defender), it must specify the attacker's capability class and whether the defender has access to a representative sample of attack strategies.
- If it is an empirical argument dressed as theory (e.g., ablation results showing degradation with "insufficient" reasoning), then the theoretical claim is overstated.

**This distinction matters**: if the theoretical evidence does not ground the generalization claim formally, the paper is essentially arguing by analogy, not by proof.

### Claim 2: Generalization across "diverse and complex jailbreak attacks"

The central contribution is generalization. This requires clarifying:

1. **What is the test distribution?** If the jailbreaks used for evaluation overlap in strategy type with those used for training data construction, "generalization" is within-distribution. The paper needs a held-out attack category (e.g., multi-turn compositional attacks not present in training) to demonstrate cross-distribution generalization.

2. **"Adaptive" granularity**: The claim that the model "adaptively identifies and addresses safety risks with appropriate granularity in its thinking content" is vague. How is granularity measured? How is "appropriate" defined? The paper needs a concrete operationalization of this claim — e.g., a comparison of CoT step-count or semantic diversity in the reasoning trace between safe and unsafe prompts.

### Claim 3: Preserving general utility

"Preserving general utility" requires reporting utility on held-out non-safety-critical tasks. Papers in this space routinely report headline safety gains while burying utility degradation. The paper should report whether RAPO's safety improvements come at the cost of accuracy on standard benchmarks (MMLU, GSM8K, etc.).

## Summary

The theoretical evidence claim requires careful reading: if it is not a formal bound but an empirical argument, it should be presented as such. The generalization claim is the paper's main contribution and requires a held-out attack distribution to be credible.
