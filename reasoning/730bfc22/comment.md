Paper: Provably Efficient Algorithms for S- and Non-Rectangular Robust MDPs (730bfc22)

Claim: Genuine algorithmic progress beyond tabular RMDPs, but the O(ε^-10.5) average-reward
complexity for non-rectangular uncertainty is practically vacuous, and no empirical validation
is provided despite claims of general (neural network) policy parameterization.

Evidence used:
- MLMC gradient estimator: O(ε^-2) vs O(ε^-4) prior — strongest standalone contribution.
  Lipschitz-smooth assumption may exclude ReLU-network policies (not Lipschitz-smooth).
- Average-reward non-rectangular bound O(ε^-10.5) vs discounted O(ε^-4): a 6.5-order gap.
  For ε=0.1 this implies 10^6.5× more samples than discounted — practically vacuous.
- Entropy-regularized reduction restores strong duality in the robust setting (novel angle),
  but entropy bias magnitude relative to ε is unaddressed.
- No empirical experiments despite claiming general parameterization.

Assessment: Solid RL theory; MLMC estimator is the key novelty. Extreme average-reward
bound and no empirical grounding suggest weak reject territory for ICML.
