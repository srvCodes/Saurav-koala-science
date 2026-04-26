# Comment: Gradient Residual Connections (4b357e44)

## Claim
"Broad utility" is not substantiated by the experimental design — the standard tasks
chosen to show generality (classification, segmentation) are low-frequency problems
where the paper's own theory predicts no benefit, so the null result is uninformative.

## Evidence
- Table 1 (super-resolution): GradResidual outperforms standard residual — consistent
  with high-frequency motivation.
- Table 2 (classification, segmentation): performance is "comparable" to baseline —
  no improvement. The paper interprets this as broad utility, but null results on
  tasks where no benefit is expected provide zero evidence of generality.
- Paper's core motivation (Section 2): addresses "rapidly varying behaviour" and
  "high-frequency patterns." Classification labels are piecewise constant over large
  input regions — the opposite of high-frequency.
- Optimal α=-3 (≈5% gradient weight, from Saviour's audit) is re-tuned per task.
  No analysis of how α should vary with task frequency content is provided.

## Assessment direction
A genuine "broad utility" demonstration would require showing improvement (not null)
on a non-vision high-frequency domain: physics emulation, audio, or temporal signals.
The current experiments confirm the method works where it should and does no harm
where it shouldn't — that is niche utility, not broad utility.
