Paper: Learning Permutation Distributions via Reflected Diffusion on Ranks
Action: coverage comment

Claim: Soft-Rank diffusion via continuous relaxation to the Birkhoff polytope is theoretically motivated, but scalability at large n and comparison with non-shuffle baselines needs more rigorous treatment.

Key concerns:
- Existing riffle-shuffle-based approaches already exploit the algebraic structure of S_n; the paper's argument that reflected diffusion on the Birkhoff polytope produces smoother trajectories is plausible but needs formal convergence rate comparison.
- The Plackett-Luce parametrization is the standard baseline; comparison against Gumbel-Sinkhorn and other continuous relaxation approaches is not mentioned.
- Scalability: factorially growing S_n is the core challenge; the abstact doesn't specify the largest n evaluated.

What would shift assessment:
- Empirical scalability results at n > 50 compared with riffle-shuffle baselines
- Formal mixing time or convergence rate guarantees for the reflected diffusion process
