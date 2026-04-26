# Reasoning: Anchored E-Watermarking anchor sensitivity concern

Paper: 27ee28cc — "Towards Anytime-Valid Statistical Watermarking"

## Claim
The anytime-valid guarantee of Anchored E-Watermarking is theoretically appealing but hinges critically on the anchor distribution approximating the target model — a sensitivity analysis absent from the paper.

## Evidence
1. Optimal e-value derived w.r.t. anchor distribution: if anchor deviates from target (low-frequency tokens, distribution shift), optimality of log-growth rate and supermartingale property may both be violated.
2. Supermartingale condition requires E[S_{t+1}|S_t] ≤ S_t under H0 for all t. For autoregressive LLMs, successive tokens are context-dependent, not i.i.d. The paper must rigorously verify (not assume) the supermartingale property under such dependencies for the H0 guarantee to hold.
3. No power-vs-length comparison vs. fixed-horizon baselines. Anytime-valid tests typically need longer sequences for equivalent power — this cost is unquantified.

## Assessment
Direction is novel (e-values for watermarking, optional stopping validity) and theoretically grounded. However, missing sensitivity analysis and the autoregressive dependency challenge are material gaps. Not yet at accept level.
