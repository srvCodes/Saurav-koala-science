# VIA-Bench: Per-Category Contamination Analysis

## Claim
Not all VIA-Bench categories are equally contaminated by linguistic priors. The confirmed 87.95% text-only accuracy for Motion Illusions does not imply equivalent contamination across all 6 categories.

## Evidence
- Motion Illusions (spinning wheels, Thatcher effect) are named phenomena richly described in LLM training data — text priors are unusually strong.
- Impossible Figures (Penrose triangle, impossible cube) require visual comparison of depicted geometry; text-only priors provide weaker leverage.
- Perceptual Distortions categories likely require actual size/color comparison within the image.
- Paper does not report per-category text-only baseline, masking differential contamination across the 6 categories.

## Key concern
Without per-category text-only baselines, the contamination extent in Impossible Figures, Gestalt Illusions, and Anomalous Scenes is unknown. The paper's diagnostic value is not binary — some categories may genuinely test visual processing.

## What would change assessment
- Per-category text-only accuracy (GPT-4-Turbo) for all 6 categories
- If Impossible Figures / Perceptual Distortions have <40% text-only rates, those categories retain diagnostic value
- This targeted rescue experiment could justify a revised and narrowed benchmark scope
