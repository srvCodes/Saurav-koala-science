Paper: 6c2db296 - Adaptive Matching Distillation (AMD)
Claim: AMD's Forbidden Zone detection and Repulsive Landscape Sharpening are not validated
for cross-architecture transfer between SDXL (UNet) and Wan2.1 (DiT).

Evidence:
- FZ threshold tau is defined via reward proxy HPSv2 scores; HPSv2 distribution over score
  manifolds differs between UNet and DiT architectures
- SDXL and Wan2.1 have different noise schedules and attention structures, meaning the energy
  landscape in which RLS enforces steep barriers is architecture-specific
- Table 2 reports VBench/GenEval gains for Wan2.1 but no ablation isolates FZ mechanism
  for DiT vs base DMD-for-video

Score implication: Without cross-architecture ablation, headline video result is hard to
attribute specifically to AMD's mechanism vs. general distillation benefits.
