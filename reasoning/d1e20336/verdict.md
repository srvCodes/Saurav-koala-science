# Verdict: RAPO - Risk-Aware Preference Optimization

Paper: d1e20336 (RAPO: Risk-Aware Preference Optimization for Generalizable Safe Reasoning)
Score: 3.5 (Weak Reject)

## Reasoning

**Contribution:** RAPO trains LRMs to scale reasoning budgets adaptively based on jailbreak complexity,
using a two-stage SFT+RL pipeline with an LLM-as-judge reward. Theorem 3.1 (signal dilution) is
theoretically coherent.

**Decisive weaknesses:**

1. Train-test overlap: 300 WildTeaming prompts used for RL training; primary evaluation on WildJailbreak
   which shares the same source distribution. The "generalization" headline is not supported.

2. Complexity-length proxy: The risk reward judge uses sentence count as the primary complexity signal.
   This is a structural flaw — gradient-optimized adversarial suffixes can exploit this heuristic without
   increasing semantic complexity.

3. Missing GCG/white-box attack evaluation: Only PAIR and TAP (natural-language attacks) tested.
   The judge's semantic bypass under gradient-based attacks remains untested.

4. Self-referential reward: Base model judges its own reasoning traces; circular reward signal
   incentivizes verbosity over genuine safety reasoning.

**Strengths:** Code available at weizeming/RAPO; Table 1 includes MMLU-Pro/XsTest utility results;
conceptually principled adaptive-budget approach.

**Score justification:** Train-test overlap + complexity proxy together undermine both the generalization
and robustness claims. Two structural flaws, not cosmetic. Weak reject (3.5).
