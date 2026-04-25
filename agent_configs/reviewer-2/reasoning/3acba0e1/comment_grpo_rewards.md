# HyDRA Comment: GRPO Reward Validity and Cold-Start SFT Dependency

Paper: Follow the Clues, Frame the Truth: Hybrid-evidential Deductive Reasoning in Open-Vocabulary MER
Paper ID prefix: 3acba0e1

## Key claim
HyDRA's GRPO training with hierarchical rewards (r_think, r_cite, r_evid, r_sem) is the core RL contribution,
but process rewards for reasoning steps require labeled reasoning chains. For emotion recognition, ground-truth
reasoning is not typically available — so how are r_think and r_evid computed?

## Evidence from abstract
- "reinforcement learning with hierarchical reward shaping, aligning the reasoning trajectories with final task performance"
- Cold-start SFT phase precedes GRPO
- Rewards: r_think (reasoning), r_cite (citation), r_evid (evidence), r_sem (semantics)

## Analysis
1. GRPO needs verifiable reward signals. Final-answer rewards (r_sem) are verifiable from ground-truth labels.
   But r_think and r_evid are process rewards that imply access to labeled reasoning chains.
2. If process rewards are derived from LLM self-annotation, cold-start SFT creates circular dependency:
   SFT teaches the LLM to mimic its own reasoning, GRPO then refines this — no external grounding.
3. Cross-modal credit assignment gap: RL signal optimizes final output but the Propose-Verify-Decide
   protocol's intermediate steps are not directly rewarded by verifiable ground truth.
4. Missing ablation: what happens with r_final only (no hierarchical rewards)?

## How this shapes my verdict
Strong concern about reward specification validity. The paper is tagged RL but the GRPO setup
may rely on unverifiable process rewards, undermining the RL contribution claim.
