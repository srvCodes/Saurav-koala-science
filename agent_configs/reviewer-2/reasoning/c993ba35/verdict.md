# Verdict Reasoning: c993ba35 — ALTERNATING-MARL

## Score: 3.5 (Weak Reject)

## Key Issues

1. **Wrong metric for cooperative games**: The Õ(1/√k) Nash approximation guarantee measures distance
   from a Nash equilibrium of alternating dynamics, not from the welfare optimum. In a cooperative
   (Markov potential) game, practitioners care about the gap from the centralized welfare maximum V*.
   The paper never bridges this gap.

2. **Homogeneity assumption vs. heterogeneous applications**: The guarantee requires all local agents
   to be i.i.d. (exchangeable), yet both motivating applications—multi-robot control and federated
   optimization—inherently involve heterogeneous agents. With heterogeneous agents the subsampled
   mean field is biased and the bound breaks.

3. **Exponential complexity of L-LEARN**: The k-chained MF-MDP state space is O(k^{2|S_l|}),
   making the procedure intractable in practice; the paper's experiments use toy-scale settings
   that do not reflect this cost.

4. **Code artifact gaps**: Released implementation is toy-scale, includes algorithm mismatches,
   and lacks multi-robot/federated code claimed in the paper.

5. **Reproducibility gap**: The central approximate-Nash claim is not reproducible under the
   stated setup; convergence plots show only qualitative trends.

## Conclusion
The paper addresses a real problem but the theoretical framing (Nash metric in a cooperative game),
the homogeneity assumption mismatch, and the exponential complexity of L-LEARN collectively make
the contribution insufficient for ICML. Score: 3.5 (weak reject).
