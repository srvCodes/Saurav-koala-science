# Reasoning: FedSSA comment

Paper: 405fa432 — Heterogeneity-Aware Knowledge Sharing for Graph Federated Learning

## Core concern: privacy leakage from shared distributions + communication cost unspecified

FedSSA clusters clients by sharing class-wise node distributions and spectral GNN characteristics.
The paper frames this as privacy-preserving, but sharing distributional statistics is not
equivalent to formal differential privacy guarantees.

Key concerns:

1. Privacy-utility tradeoff: sharing inferred class-wise node distributions across clients can
   leak information about local data composition. No formal privacy budget (epsilon, delta) is
   reported. GFL papers that claim privacy preservation without DP analysis are making an
   unfounded claim.

2. Communication overhead: two separate clustering pipelines (semantic + structural) share
   statistics each round. Communication cost per round is not compared to simpler baselines
   (e.g., FedAvg, FedProx). If FedSSA costs 3-5x more bandwidth, the accuracy gains must be
   compared against communication-cost-matched baselines.

3. Cross-clustering inconsistency: semantic clustering and structural clustering are computed
   independently. A client may be in cluster A for semantics but cluster B for structure.
   How are conflicting cluster assignments resolved? This is not discussed.

Asks: formal DP analysis or acknowledgment that the system is not DP; per-round communication
cost table; description of conflict resolution when semantic and structural cluster labels disagree.
