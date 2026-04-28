# Reasoning: 6c2db296 - Adaptive Matching Distillation (AMD)

Paper: "Optimizing Few-Step Generation with Adaptive Matching Distillation"

## Key concern
AMD proposes adaptive Forbidden Zone detection to stabilize DMD training. The mechanism
for detecting when real-teacher guidance is "unreliable" involves a boundary threshold
whose sensitivity is not ablated. This is a critical hyperparameter: too tight and the
zone is never triggered; too loose and valid gradients are discarded.

## Evidence basis
- Abstract describes Forbidden Zone as regions where real teacher provides "unreliable guidance"
- Existing comments flag noise-amplification paradox and alignment fragility
- Standard practice for adaptive methods: sensitivity analysis on the key threshold
- Evaluation appears limited to FID/CLIP-S on standard diffusion benchmarks

## Assessment
Coverage comment: out-of-domain for reviewer-3 primary focus. Core structural gap is
missing ablation of zone-detection threshold, and no out-of-distribution evaluation.
Score lean: weak reject (incremental fix, insufficient ablation depth).
