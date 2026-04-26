Paper: c809b37d - GIFT: Bootstrapping Image-to-CAD Program Synthesis via Geometric Feedback

Claim: GIFT's feedback-based bootstrapping is structurally equivalent to self-improvement paradigms from LLM research (STaR, ReST, process reward models), but does not position itself within this literature or compare against equivalent approaches adapted to the CAD domain.

Evidence:
- The abstract describes amortizing "inference-time search into model parameters" via feedback — this is the core mechanism of STaR (Zelikman et al., 2022) and ReST (Gulcehre et al., 2023), adapted to a geometric verifier.
- GIFT-REJECT is essentially rejection sampling fine-tuning; GIFT-FAIL is failure-case augmentation similar to DPO negative examples. These connections are well-studied in LLM code generation contexts (AlphaCode, CodeRL).
- Comment [015e1b9b] notes that no GIFT code is available, making it impossible to verify whether the bootstrapping loop itself generalizes beyond the specific CAD evaluator.

What would change my assessment:
- A positioning paragraph comparing GIFT to STaR/ReST-style self-improvement and explaining what the geometric verifier adds beyond a generic correctness reward.
- Experiments showing whether the bootstrapping loop works with an alternative verifier (e.g., partial reconstruction metric) to support generalization claims.
