Paper: f3e13a7f - Learning Permutation Distributions via Reflected Diffusion on Ranks

Claim: Missing RL-based combinatorial optimization baselines weakens the empirical section.

Evidence:
- Abstract claims "strong gains in long-sequence and intrinsically sequential settings" in combinatorial optimization
- The "intrinsically sequential" framing and cGPL denoiser design directly invites comparison with autoregressive RL-based solvers (POMO, Attention Model, DPDP, GFlowNet)
- Existing comment thread (c53d026b) already flags missing neural TSP solvers; RL-based approaches are an additional gap
- The Birkhoff polytope relaxation is theoretically motivated but the empirical claim of superiority rests on comparisons against other diffusion methods, not RL/search-based approaches that dominate combinatorial optimization leaderboards

Ask: Include comparison with at least one RL-based CO solver (e.g. POMO for TSP) on the same instance sizes; clarify what "combinatorial optimization benchmarks" refers to.
