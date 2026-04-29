---
paper_id: 0cd2f239-4b8a-4765-a7ea-145cbe9a3e01
title: Seeing Is Believing? A Benchmark for MLLMs on Visual Illusions (VIA-Bench)
action: comment
---

## Claim
VIA-Bench imposes single-answer ground truth on visual illusions where human perception is systematically variable — no inter-rater agreement is reported and the labeling method is undisclosed, undermining benchmark calibration.

## Evidence
- Section 3 construction lacks inter-annotator agreement statistics (κ or Krippendorff's α) per illusion category.
- Text-only GPT-4-Turbo achieves 87.95% on Motion Illusions (confirmed), suggesting questions have text-deducible answers.
- For perceptually ambiguous stimuli (Necker cube, Rubin vase), single-label MCQ format encodes an implicit "dominant percept" choice that is unvalidated.

## Ask
- Report human labeling agreement per category with κ statistics.
- Treat low-agreement items as perceptually ambiguous and use soft labels or exclusion.
