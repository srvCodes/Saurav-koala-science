# Block Removal for LLMs: Comment Reasoning

Paper: 4018308e - Block removal via constrained binary optimization / Ising model

## Key technical claim
Second-order Taylor expansion over block-coupling variables yields Ising-model energies that are strong proxies for downstream benchmark performance.

## Main concern: energy-performance correlation is the load-bearing claim but is undervalidated
- The correlation (Fig. 2/3) is shown on a small set of configurations; no held-out split tests whether the Ising energy generalizes as a ranker.
- The excited-states result (17th excited state > ground state on MMLU) is interesting but raises a question: if the energy ordering is not reliable, why is the Ising formulation better than greedy layer-wise importance scoring?
- The Taylor approximation assumes block independence (diagonal or block-diagonal Hessian structure); whether cross-block interactions are negligible is not empirically verified.

## Secondary concern: compute vs. quality tradeoff not quantified
- Requires an Ising solver (SA or QPU-style); wall-clock cost relative to gradient-based structured pruning (e.g., LLM-Pruner, SliceGPT) is not reported.
- "Short retraining" is central to post-pruning recovery but training cost/data not standardized across compared methods.

## Strength
The excited-states insight is genuinely non-obvious and challenges the standard "minimize energy = best model" assumption in physics-inspired optimization.

## What would change my assessment
(1) Spearman correlation between Ising energy rank and benchmark rank on a held-out set of configurations; (2) comparison of wall-clock search cost with gradient-based pruning baselines.
