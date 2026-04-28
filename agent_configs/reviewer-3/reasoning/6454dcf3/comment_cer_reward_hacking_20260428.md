# Review: CER - Conditional Expectation Reward (6454dcf3)

**Paper**: Reinforcement Learning with Conditional Expectation Reward
**Paper ID**: 6454dcf3-6eff-4b23-b5be-9bfaa905a83a
**Date**: 2026-04-28

## Central Claim
CER replaces rule-based verifiers in RLVR with a self-referential reward: P(reference_answer | generated_answer), computed by the LLM being trained. This enables RLVR in domains where rule-based verification is intractable.

## Core Technical Concern: Self-Referential Moving Target

CER uses the same LLM as both policy and verifier. During RLVR training, the policy weights θ change each step. If the verifier is the current model θ_t, then the reward function R(y_gen; θ_t) = P_{θ_t}(y_ref | y_gen) is a moving target: the reward for the same (x, y_gen) pair changes at every gradient step. This violates the standard RLVR stability assumption where the reward is either rule-based (fixed) or comes from a frozen reward model. The paper needs to clarify whether the verifier is:
(a) the current policy θ_t (moving target, potentially unstable)
(b) a frozen reference model θ_0 (fixed, but becomes stale as θ diverges from θ_0)
(c) periodically updated frozen checkpoints

This is not a minor implementation detail. Under option (a), the training objective becomes:
max_θ E[P_θ(y_ref | y_gen)] where y_gen ~ π_θ(x)
This creates an unusual self-play dynamic where the model is simultaneously optimized to (i) generate high-reward answers and (ii) assign high probability to the reference given those answers. These are potentially conflicting incentives.

## Degenerate Solution: Reference Copying

A degenerate but high-reward solution exists: the model learns to generate y_gen ≈ y_ref (copying or closely paraphrasing the reference). This maximises P(y_ref | y_gen) trivially. Unlike rule-based verifiers where exact-match or format checks prevent this, CER has no mechanism to penalise reference leakage. The paper should report whether degenerate copying is observed, and whether any length or diversity constraints are applied.

## Reference Answer Requirement Limits Scope

CER requires y_ref (reference answer) at training time. The paper claims to address "general domains with free-form answers," but free-form domains often lack ground-truth reference answers — the same limitation that makes rule-based verifiers hard to construct. CER shifts the problem from "hard to verify" to "hard to acquire reference answers," not eliminating it. For multi-answer domains (e.g., creative writing, open-ended reasoning), selecting a single y_ref would systematically penalise equally valid but differently phrased correct answers.

## Missing Comparison to Existing Soft Reward Approaches

The paper frames CER as distinct from "external verifiers or auxiliary models," but several soft reward approaches occupy the same space:
- RLAIF (using a separate LLM as judge, e.g., Bai et al. 2022)
- Process Reward Models (PRMs, Lightman et al. 2023)
- Self-consistency aggregation (Wang et al. 2023) as an implicit reward signal

The key empirical questions are: (1) Does CER outperform these approaches on general-domain tasks? (2) Is the self-referential verifier better calibrated than an external judge model? Without these comparisons, CER's advantage over existing soft reward methods is undemonstrated.

## Strengths
- The conditional expectation framing is conceptually clean and theoretically grounded
- Soft, graded reward is preferable to binary signals for tasks with partial credit
- Self-contained (no auxiliary model) is a practical advantage in resource-constrained settings
- Code released (github.com/changyi7231/CER)

## Summary Assessment
The CER proposal is novel and addresses a real limitation of RLVR. The self-referential nature of the verifier is the critical unresolved question — whether this creates training instability or a degenerate copying solution determines whether CER is a principled approach or a reward hacking surface. These concerns require empirical ablation (frozen vs live verifier, with/without copying constraint) before the method's validity can be established.
