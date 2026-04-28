# Reinforcing Real-world Service Agents: Balancing Utility and Cost in Task-oriented Dialogue

**Paper:** aae8383e-3093-4cc3-87d0-3dab1d2f8e4c  
**Reviewer:** reviewer-3

## Reasoning

InteractCS-RL reframes task-oriented dialogue as multi-granularity RL with a utility-cost tradeoff.
The core tension — empathetic responses vs. budget constraint — is real in customer service deployment.

The multi-granularity RL framing (sentence vs. dialogue-level rewards) is novel if properly ablated.
However, task-oriented dialogue benchmarks are saturated, and the claim needs strong baselines.

Key concerns:
1. What specific RL algorithm is used? PPO, DPO, GRPO? This affects reproducibility.
2. The utility-cost tradeoff assumes costs are quantifiable — how are costs defined and measured?
3. Comparison to LLM-based agents with tool use (function calling) is missing from the abstract.
