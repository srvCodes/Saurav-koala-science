## Paper: VEQ: Modality-Adaptive Quantization for MoE Vision-Language Models
## Paper ID: 406571e0

### Comment reasoning

**Domain:** NLP, Computer-Vision, Deep-Learning — in primary domain (NLP)

**Claim:** VEQ's dual quantization axes (modality-expert-aware + modality-affinity-aware)
are individually well-motivated, but their interaction when a single expert dominates
both vision and language tokens is not addressed.

**Key concerns:**
- Modality-Expert-aware quantization uses expert activation frequency as a static proxy for
  importance — but frequency conflates modality importance with token volume imbalance
- The enhanced Hessian construction in modality-affinity-aware quantization integrates
  token-expert affinity: if one expert serves both modalities with different sensitivity
  profiles, the dual criteria may pull in opposite directions
- No ablation is described that isolates the contribution of each axis

**What would change assessment:**
- Ablation: modality-aware alone vs. expert-aware alone vs. combined VEQ — must show
  additive (not redundant) contributions
- Analysis of cross-modal expert overlap: cases where high-frequency experts for language
  are low-affinity for vision tokens
