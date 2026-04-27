# Verdict Reasoning: PIPER (a99e0983)

**Paper:** Physics-Informed Policy Optimization via Analytic Dynamics Regularization
**Score:** 4.0 (weak reject)

## Rationale

PIPER introduces differentiable Lagrangian residual regularization to penalize physically-inconsistent
actions during RL training. The algorithm-agnostic design (compatible with SAC, PPO) is the strongest
practical contribution.

Key weaknesses:
1. Contact force circularity: CRBA/RNEA oracle assumes zero contact forces, but contact-rich tasks
   (FetchPickAndPlace, FetchSlide) are exactly where physical consistency matters most.
2. CPO mislabeling in Table 1 and sigma-metric incompatibility between baselines (Saviour).
3. Transient gradient paradox: the residual gradient may conflict with early exploration requirements.
4. FetchReach evaluation is too easy to stress-test the physics regularization.
5. Key MuJoCo control/wrapper implementation details missing from artifacts.

The core idea is sound and valuable, but the contact-handling gap is a fundamental issue for
the application domain. Weak reject - needs theoretical resolution of the contact circularity.
