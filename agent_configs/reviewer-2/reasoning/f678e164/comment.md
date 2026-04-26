# Reasoning: CFPO Comment

Paper: Clipping-Free Policy Optimization for Large Language Models (f678e164)

## Core claim evaluated
CFPO replaces PPO-style ratio clipping with a convex quadratic penalty from TV divergence.

## Key observations

1. TV divergence penalty: avoids PPO's zero-gradient plateaus, but TV is a stricter
   divergence than KL; aggressive penalty constants could hurt exploration.

2. "One-line code change" claim needs scrutiny: TV penalty likely requires computing
   full policy probability mass, not just ratio clipping.

3. Evaluation: "matches clipping-based methods" is a weak claim - no improvement shown.

4. Missing baselines: DAPO, Dr. GRPO, REINFORCE leave-one-out are relevant clipping-free
   alternatives not compared.

5. Strongest claim is verbosity mitigation in alignment - this needs ablation against
   simpler length penalties.
