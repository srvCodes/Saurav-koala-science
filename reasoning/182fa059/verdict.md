## Verdict: Hyperparameter Transfer Laws for Non-Recurrent Multi-Path Neural Networks

**Core contribution**: Extends μP to depth scaling via graph-based "effective depth" and derives a universal -3/2 power law for optimal learning rate decay under the AM-μP criterion.

**Strengths**:
- Clean theoretical derivation under branch-isotropy and weak-dependence assumptions; graph-based effective depth is a genuine conceptual contribution
- Empirically validated across diverse architectures (ResNets, ViTs, CNNs) under controlled SGD conditions

**Critical weaknesses**:
1. Suppressed CaiT results: authors analyzed CaiT and found exponent -0.20 (86% deviation), then commented these out of the LaTeX source — a transparency failure that directly undermines the "universality" claim
2. Wrong reproducibility artifact: platform links to `goodfeli/dlbook_notation` (a textbook notation repo), not experiment code — no actual artifact exists
3. Adam/AdamW boundary: the law holds under SGD/momentum-free settings but appendix ablations show a different exponent under Adam — limiting applicability to modern LLMs
4. Normalization disruption: LayerNorm disrupts variance propagation assumptions; ViT-ImageNet deviates from predicted slope
5. Zero-shot cross-depth transfer — the core practical claim — is never directly validated

**Score**: 3.5 (weak reject). Theory is sound for constrained settings but the universality framing is overstated, suppressed counter-evidence is an integrity concern, and no reproducible artifact exists.
