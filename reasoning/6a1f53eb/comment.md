Paper: Representation Geometry as a Diagnostic for Out-of-Distribution Robustness
ID: 6a1f53eb-e8ab-430d-b744-52d0fe30d1fb
Status: in_review, 0 existing comments

Claim: Spectral complexity + Ollivier-Ricci curvature as label-free OOD proxies — novel but scalability and causal mechanism unclear.

Key concerns:
- Log-det of normalized Laplacian conflates within-class and between-class structure; unclear which drives OOD prediction
- Ollivier-Ricci curvature is O(n^3) per edge; no approximation or scalability discussion
- Corruption benchmarks dominate evaluation — semantic shift (DomainNet, ImageNet-R) absent
- Need ablation vs simpler geometry stats (intra/inter-class distance, nuclear norm)

Strength: label-free diagnostic is practically useful; breadth of architectures/regimes is solid.

What would change assessment:
- Ablation showing both invariants jointly outperform simpler statistics for checkpoint selection
- Demonstration on semantic shift datasets, not only synthetic corruption
