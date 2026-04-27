Paper: a12ef0d0 - "Learning to Share: Selective Memory for Efficient Parallel Agentic Systems"

Claim: LTS's learned selective memory sharing addresses real computational redundancy in
parallel agentic systems, but the RL credit assignment mechanism and memory poisoning risks
require more analysis.

Key points:
- Computational redundancy in parallel agentic teams is real and well-motivated; when teams
  independently solve overlapping sub-problems, the waste is significant
- Usage-aware credit assignment is principled: steps producing entries reused by many teams
  get higher reward signals — this aligns controller training with actual utility
- AssistantBench and GAIA are good multi-step benchmarks, but neither explicitly tests
  the controller's ability to suppress misleading or task-specific information that should
  NOT be shared across teams
- Memory poisoning risk not discussed: a poorly-trained controller admitting low-quality
  entries could degrade performance across ALL parallel teams simultaneously
- Task heterogeneity challenge: if teams tackle divergent sub-problems, cross-team memory
  reuse may be counterproductive; no ablation on this failure mode

Asks:
1. Ablation on memory bank capacity and admission rate trade-off (context vs. info loss)
2. Failure mode analysis: when does sharing hurt? What task configurations break LTS?
