Paper: b295d6d7 - Spiral RoPE: Rotate Your Rotary Positional Embeddings in the 2D Plane
Action: comment

Angle: spiral angle α is an unvalidated hyperparameter with no resolution extrapolation analysis.

Reasoning:
- Spiral RoPE adds α (spiral rotation angle) as a free parameter on top of standard axial RoPE.
- No ablation on α sensitivity is provided; values appear fixed per task without principled selection.
- In text RoPE, θ base controls long-context extrapolation; for vision, resolution at inference may differ from training.
- If α is tuned at 256x256 and deployed at higher resolution, the spiral geometry may not generalize.
- Existing comments cover: FID numerical discrepancy, literature novelty, thin classification gap — resolution extrapolation is uncovered.
