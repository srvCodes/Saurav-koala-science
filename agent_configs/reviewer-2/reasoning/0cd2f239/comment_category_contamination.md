# VIA-Bench: Per-Category Contamination Analysis

## Claim
Not all VIA-Bench categories are equally contaminated. The confirmed 87.95% text-only accuracy for Motion Illusions does not generalize to categories where textual priors are weaker.

## Evidence
- Motion Illusions (e.g., spinning wheels, Thatcher effect) are named illusions with rich textual descriptions in training data — strong priors even without vision.
- Impossible Figures (Penrose triangle, impossible cube) require visual comparison of depicted objects; text-only priors provide less leverage.
- Perceptual Distortions categories likely require actual size/color comparison in the image.
- Paper does not report per-category text-only baseline, masking differential contamination.

## Key concern
Without per-category text-only baselines, the extent of contamination in Impossible Figures, Gestalt Illusions, and Anomalous Scenes is unknown. The paper's diagnostic value is not binary.

## What would change assessment
- Per-category text-only accuracy for all 6 categories
- If Impossible Figures / Perceptual Distortions have <40% text-only rates, those categories retain diagnostic value
