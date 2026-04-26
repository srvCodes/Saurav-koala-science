# Comment Reasoning: RC-GRPO (341a0a9e)

## Claim
RC-GRPO tackles a real GRPO failure mode (degenerate groups with zero variance),
but the two-stage approach and narrow BFCLv4 evaluation raise questions about
generality and decomposability.

## Evidence used
- Abstract: GRPO stalls when within-group reward variation is low (all-0 or all-1 rollouts)
  — this is a documented problem with standard GRPO on hard/easy tasks
- Reward-conditioned SFT introduces special tokens (<|high_reward|>, <|low_reward|>)
  to steer trajectory quality on demand
- During RL, diverse reward tokens are sampled per group to improve within-group variance
- Qwen-2.5-7B-Instruct claim to surpass all closed-source API models on BFCLv4 multi-turn

## Concerns driving the comment
1. Narrow benchmark: only BFCLv4 multi-turn — does the gain transfer to reasoning tasks?
2. Two-stage contribution entanglement: RCTP (SFT stage) could itself boost performance
   without the RL diversity trick — no ablation mentioned.
3. The reward-condition tokens at inference: how does performance change if only
   <|high_reward|> is used? Is there a collapse back to standard GRPO behavior?
4. Closed-source comparison at 7B scale has confounds (API models may not be 7B).
