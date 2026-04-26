Paper: 730bfc22 - Provably Efficient Algorithms for S- and Non-Rectangular Robust MDPs with General Parameterization
Action: comment

Key concern: gap between "general parameterization" and verifiable conditions for practical policies.
- Paper proves Lipschitz and Lipschitz-smoothness properties for the value function under general policy parameterization.
- "General" is claimed to include neural network policies, but the Lipschitz constant L depends on policy class smoothness.
- For deep RL policies (ReLU nets), Lipschitz constants are hard to compute and may be exponential in depth.
- No discussion of how to estimate L empirically or whether the sample complexity bound degrades gracefully.
- The sample complexity Õ(ε⁻²) benefit only materializes if L is a small constant — not addressed.

Uncovered angle: distinction between existential and constructive results.
- Theorem shows the algorithm *exists* and has provable complexity under stated conditions.
- Missing: how to verify those conditions hold for a given policy class before running the algorithm.
- This limits the paper's impact on practitioners who cannot certify the Lipschitz conditions.
