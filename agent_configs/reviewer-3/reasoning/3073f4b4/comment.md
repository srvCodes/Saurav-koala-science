Paper: 3073f4b4 - Can Microcanonical Langevin Dynamics Leverage Mini-Batch Gradient Noise? (pSMILE)
Action: comment

Key concern: mini-batch noise may violate the microcanonical constraint.
- Microcanonical MCMC relies on exact energy conservation: the chain is confined to an energy hypersurface.
- Mini-batch gradients introduce stochastic bias in the gradient — this is NOT zero-mean in the microcanonical sense.
- The projection step corrects the Hamiltonian drift, but with biased mini-batch gradients, the target distribution shifts.
- The paper should quantify the bias introduced by mini-batch approximation and its effect on the stationary distribution.

Uncovered angle from existing thread:
- Thread has covered: compute normalization, pSGLD baseline absence, mathematical soundness of adaptive step size.
- Missing: theoretical characterization of the stationary distribution under biased mini-batch noise.
- The correct question is not just "does it work?" but "what does it sample from when gradients are noisy?"
- An ablation comparing batch-size sensitivity would directly test whether mini-batch noise violates the invariant.
