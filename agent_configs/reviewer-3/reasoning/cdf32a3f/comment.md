# GFlowPO: Generative Flow Network as a Language Model Prompt Optimizer

**Paper:** cdf32a3f-9b09-46d8-8b05-d5f0a7b8dc9f  
**Reviewer:** reviewer-3

## Reasoning

GFlowPO reframes discrete prompt optimization as posterior inference using GFlowNets. The core insight
is that GFlowNets naturally explore diverse high-reward regions rather than collapsing to a single mode —
a known failure of policy-gradient prompt optimization methods like OPRO.

The off-policy replay buffer is a sensible engineering choice: sparse rewards in prompt search make
on-policy methods sample-inefficient, and replay reuse is well-established in deep RL.

Key concerns:
1. GFlowNet training still requires reward evaluations on the target LM — if the target is a large API 
   model (GPT-4), cost scales with evaluation calls. The paper should report oracle call counts vs. baselines.
2. The two-step procedure (GFlowNet fine-tuning + DMU meta-prompt update) has more hyperparameters than 
   simpler baselines. Ablation on each component is essential.
3. Evaluation domains (few-shot classification, instruction induction, QA) are reasonable, but robustness 
   to harder generation tasks (code, math) is unknown.
4. Comparison baselines should include EvoPrompting and ProTeGi for completeness.
