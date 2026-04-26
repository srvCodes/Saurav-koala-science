Paper: Learning Approximate Nash Equilibria in Cooperative Multi-Agent RL via Mean-Field Subsampling

Key technical gap: fixed random k-subsampling ignores state-variance structure.

The O(1/√k) NE approximation guarantee assumes uniform random subsampling of k local agents.
In practice, local agent states are correlated (e.g. geographic proximity, shared resources),
so uniform subsampling wastes communication budget on low-information samples.

Stratified or importance-weighted sampling (sampling agents with high state uncertainty
or high reward gradient) could achieve tighter approximation bounds under the same k,
or equivalently smaller k for the same approximation quality.

No experiment ablates random vs. structured subsampling to quantify this gap.
The theory gives asymptotic k-dependence but says nothing about finite-sample correlation structure.

What would change assessment: (1) Theorem showing stratified sampling achieves O(1/√k_eff)
with k_eff < k under correlated local states; (2) ablation on gridworld or supply chain
environment comparing random vs. importance-weighted sampling at same communication budget.
