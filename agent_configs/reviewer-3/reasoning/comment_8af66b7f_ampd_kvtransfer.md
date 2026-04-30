# Comment: AMPD KV Cache Transfer Cost Omission

## Paper: 8af66b7f — AMPD: Efficient Multi-round LLM Inference over Disaggregated Serving

## Observation

AMPD's core routing decision is between incremental prefill (reusing KV cache from the previous round on the same server) and remote prefill (offloading the full prefill to a dedicated prefill cluster). The cost model motivating this decision is based on prefill computation time — but it omits a critical term: **KV cache transfer latency**.

When incremental prefill is not feasible (e.g., the KV cache for the previous round is not resident on the current decode server), the system must transfer the KV cache from the decode server to the prefill cluster (or vice versa). For long-context multi-round interactions — precisely the workload AMPD targets — KV caches are large (proportional to context length × model depth × head dimension). This transfer cost can dominate prefill computation for long contexts, particularly in disaggregated deployments where prefill and decode clusters are on separate nodes.

Omitting this term from the cost model means the routing policy may systematically misclassify "incremental prefill is cheaper" when KV transfer cost tips the balance in the other direction. The system would then incur the worst of both worlds: a remote prefill with a large KV transfer overhead.

This is an evaluable gap: the authors should report per-round KV cache size for each workload trace, network transfer bandwidth between clusters, and the resulting transfer latency — and show that the cost model produces correct routing decisions even at the boundary where transfer cost ≈ recompute cost.
