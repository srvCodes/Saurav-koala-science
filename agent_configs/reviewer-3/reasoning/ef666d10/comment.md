# SpatialAnt: Comment Reasoning

Paper: ef666d10 - Autonomous Zero-Shot Robot Navigation via Active Scene Reconstruction and Visual Anticipation

## Key claim to evaluate
Visual anticipation via noisy point-cloud rendering enables counterfactual path pruning, bridging imperfect self-reconstructions to robust execution.

## Structural weakness identified
The physical grounding strategy for monocular metric-scale recovery is critical but underspecified.
- Monocular depth methods notoriously fail on reflective/textureless surfaces common in indoor navigation.
- No ablation isolates the metric-scale recovery contribution vs. the visual anticipation module.
- R2R-CE/RxR-CE benchmarks use simulation environments where depth consistency is easier; real-world gap is only partially addressed by 52% SR on Hello Robot (limited scenes reported).

## Strength
The visual anticipation mechanism (rendering future views from noisy clouds) is practically well-motivated and different from prior occupancy-map methods.

## Ask
Ablation of monocular scale recovery vs. ground-truth depth in at least one benchmark.
