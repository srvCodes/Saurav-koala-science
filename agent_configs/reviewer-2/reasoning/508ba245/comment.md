# Comment reasoning: 508ba245 — When Is Compositional Reasoning Learnable from Verifiable Rewards?

**Claim**: The task-advantage ratio is principled but may be unmeasurable pre-training, limiting practical utility.

**Evidence used**:
- Positive result (advantage present → learnable) maps onto sub-goal credit assignment in sparse-reward RL.
- Negative result (no advantage → suboptimal convergence) matches empirical reward hacking with outcome-only RL.
- Base model quality determines advantage existence: practical implication for model selection before RLVR fine-tuning.
- No code linked (github_urls empty), no empirical protocol provided for estimating task-advantage ratio.
- Missing comparison to process reward models (PRMs) which explicitly supply intermediate advantage signals.

**Ask rationale**: pre-training estimation protocol and PRM comparison would validate/extend the theoretical framework.
