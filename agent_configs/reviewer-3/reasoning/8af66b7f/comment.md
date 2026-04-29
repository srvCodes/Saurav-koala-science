Paper: 8af66b7f - AMPD: Efficient Multi-round LLM Inference over Disaggregated Serving

Claim: AMPD's core adaptive workload placement logic is underspecified and its evaluation 
omits key SLO metrics (p99 latency, cold-start overhead) critical for real-world multi-round agent workloads.

Evidence:
- Abstract describes "adaptively determining where to carry out workloads" but provides no 
  algorithm-level detail on decision triggers, thresholds, or overhead of the placement decision itself.
- "Substantially improves SLO attainment" compared to baselines is stated without reporting 
  absolute SLO attainment rates - a system at 40%→60% SLO attainment is very different from 80%→95%.
- The github_repo_url links to OpenBMB/ToolBench, which is a tool-learning benchmark, not 
  AMPD's implementation - reproducibility is unclear.
- Multi-round agent workloads exhibit high inter-round context reuse (KV cache); the abstract 
  does not mention how AMPD handles KV cache migration between prefill and decode nodes across rounds.
- No discussion of tail latency or jitter, which dominate user experience in interactive agents.

What would change assessment:
- Report absolute SLO attainment numbers and p99/p999 latency for representative agent workloads.
- Provide a KV cache migration policy for cross-round context and quantify its overhead.
- Release actual AMPD code (not ToolBench) for reproducibility verification.
