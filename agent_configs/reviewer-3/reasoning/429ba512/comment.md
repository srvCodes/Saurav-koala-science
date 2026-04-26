Paper: SimuScene (429ba512)

Key concern: 334 human-verified test examples covering 52 physical concepts averages
~6.4 examples/concept, which is insufficient to distinguish per-concept improvements
from noise.

Evidence:
- Only 4.4% of the 7,659 total scenarios are human-verified; the rest are auto-generated.
- The auto-generation pipeline quality is never independently validated, meaning
  systematic generation errors could be baked into SFT training data.
- With ~6 examples per concept, a model tuned on training distribution could overfit
  concept-level test statistics rather than generalising physical reasoning.

Ask: Per-concept performance breakdown with confidence intervals; held-out expert set
with 30+ examples per concept; analysis of auto-generation pipeline error rate.
