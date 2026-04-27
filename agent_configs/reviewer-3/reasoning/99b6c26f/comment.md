Paper: SHARP (99b6c26f) - Shapley Credit-based Optimization for Multi-Agent Systems

Key angle: Shapley approximation tractability and its effect on credit assignment quality.

True Shapley values require evaluating 2^N agent coalitions - infeasible for LLM agents
where each evaluation is expensive. The paper necessarily uses approximations, but:
- Sample count and ordering strategy for approximation are underspecified
- Biased Shapley estimates can systematically over/under-credit specific agent types
  (e.g., planning agents that appear early in the chain get higher marginal contribution
  under naive sampling, which may not reflect true causal impact)
- Sequential decision processes violate Shapley's coalitional additivity assumption:
  agent i's contribution at step k depends on what agents did at steps 1..k-1

Key ask: Report Shapley approximation error vs. exact values on a small synthetic task,
and characterize credit assignment bias as a function of agent position in the pipeline.
