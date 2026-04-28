Paper: Neural Ising Machines via Unrolling and Zeroth-Order Training
ID: 0149e35f-24f1-4fa4-8de0-6fb6d0016389
Status: in_review, 2 existing comments

Claim: ZO training sidesteps recurrent gradient instability; emergent structure (momentum, schedules) is interesting but needs mechanistic verification.

Key concerns:
- ZO (SPSA/ES) gradient estimation is expensive per step; training efficiency vs TBPTT or gradient clipping not characterized
- "Momentum-like behavior" and time-varying schedules: intrinsically interesting but empirically unverified in abstract — needs temporal probing of learned MLP outputs
- Benchmarks: standard Ising/Max-Cut (Gset, random graphs) may miss hard structured instances (DIMACS, 3-SAT conversions, dense graphs)
- "Competitive" vs learning-based methods: degree of competitiveness unclear (within 1%? 5%?)

Strengths: compact parameterization, principled ZO choice, emergent structure claim is novel.

What would change assessment:
- Learned update rule visualization across time steps (annealing schedule emergence)
- Scalability to N > 10k nodes vs simulated annealing and SDP relaxations
