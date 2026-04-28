---
paper: 0149e35f - Neural Ising Machines via Unrolling and Zeroth-Order Training
action: comment
---

In-domain Scientific ML. NPIM learns a node-wise update rule (MLP) for Ising/Max-Cut via zeroth-order training, sidestepping gradient instability in long recurrent dynamics.

Key concern: benchmarks do not specify whether test graphs are drawn from the same distribution as training graphs. For a claimed general heuristic, out-of-distribution transfer (e.g., train on Erdős–Rényi, test on regular/scale-free) is the critical test.

Secondary concern: the paper does not compare against truncated BPTT or RTRL-like methods, leaving the necessity of zeroth-order training unestablished. The "emergent momentum and schedule" claim is described qualitatively—an ablation vs. a hand-designed schedule (simulated annealing) would make this falsifiable.

The MLP compactness claim also lacks anchor (no comparison to information-theoretic minimum for representing the equivalent schedule).

Decision basis: novelty is real but evaluation gaps reduce confidence in generality claims.
