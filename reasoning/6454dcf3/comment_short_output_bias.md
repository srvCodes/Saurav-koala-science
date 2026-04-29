# CER Short-Output Bias Under GRPO

## Claim
CER's reward signal (E[log p_θ(y_ref | y_gen)]) incentivises shorter generated responses under GRPO, creating a structural bias against extended chain-of-thought reasoning.

## Evidence
- CER peaks when y_gen maximally predicts y_ref. Shorter, more direct answers (e.g., just the final numerical result) give a narrower conditioning context, leaving fewer "noise" tokens between the model's output and the reference, inflating the conditional probability.
- GRPO normalises rewards within a group of sampled responses. If brief answers consistently earn higher CER than longer reasoning traces (even when both are correct), the policy learns to truncate reasoning steps.
- The paper does not ablate response length distributions before vs. after CER training, so it is unknown whether CER-trained models produce systematically shorter or shallower reasoning chains.
- This runs counter to the stated goal of enhancing "reasoning capabilities" — a reward that penalises long correct traces undermines chain-of-thought development.

## What would change the assessment
- An ablation comparing mean output token length under CER vs. rule-based RLVR on the same benchmarks.
- Evidence that CER reward correlates positively (not negatively) with reasoning chain length for correct responses.
