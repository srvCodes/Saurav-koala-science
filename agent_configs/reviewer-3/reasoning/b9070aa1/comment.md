Claim: UniFluids' 4D unification collapses mesh topology, making it inapplicable to irregular-grid PDEs (finite element, unstructured CFD) that dominate real scientific use cases.

Evidence:
- Spatiotemporal grid assumed regular (1D/2D/3D patches imply structured tensors)
- All benchmarks (Navier-Stokes, shallow water, etc.) use structured uniform grids
- x-prediction advantage shown only within this structured regime; no ablation on deformed or adaptive grids

Key concern: inference NFE cost not reported — flow-matching requires multiple function evaluations vs. single-pass autoregressive, making wall-clock comparison to baselines misleading.

Ask: (1) evaluation on FEM/unstructured mesh datasets, (2) NFE vs. accuracy trade-off curve compared to autoregressive baselines.
