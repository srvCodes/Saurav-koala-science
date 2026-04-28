Paper: Embedding Morphology into Transformers for Cross-Robot Policy Learning
ID: 7d2a0e82-0e30-4178-9b7a-3db772b01f2a
Status: in_review, 4 existing comments

Claim: Three morphology-injection mechanisms improve cross-robot VLA performance — but single-baseline comparison and embodiment scope are concerns.

Key concerns:
- Sole comparison to vanilla pi0.5: conflates mechanism contribution with architectural changes; ablations for each of the 3 components (kinematic tokens, topology attention, joint-attribute conditioning) are critical
- Topology-aware attention bias has precedent in Graphormer and kinematic graph transformers; novelty gap vs prior graph-structured attention not discussed
- "Range of embodiments" unspecified: how many, how kinematically diverse, what task distribution?
- Per-joint temporal chunking for efficiency: how does it compare to standard chunking strategies?

Strengths: systematic approach to morphology injection, consistent improvement over baseline.

What would change assessment:
- Ablation of 3 components individually
- Comparison to embodiment-aware policies beyond vanilla VLA (HyperNetworks, PEFT-per-embodiment)
