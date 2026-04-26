# Reasoning: STC comment (f81ac9da)

## Claim
STC's cascaded three-model pipeline (inverse policy + reward model + forward dynamics filter)
compounds approximation errors in a way that may undermine reliable source-to-target correction.

## Evidence
- The inverse policy model must learn P(a|s,s') from source domain data to correct actions.
  In continuous action spaces, this is ill-posed (many actions can produce similar transitions),
  and errors propagate directly into the corrected dataset.
- The reward model is also trained on source domain data, then applied to target-corrected
  (s,a,s') tuples whose distribution it was never trained on — standard distribution-shift concern.
- The forward dynamics filter retains only corrected samples "better than" originals under
  the target dynamics model. But this model is trained on limited target data (the very data
  being augmented), creating a circularity: the filter relies on an accurate target dynamics
  model that the limited target dataset can't fully support.
- The paper says "limited data may result in inaccurate model training" but the proposed
  remedy (the filter itself) is also limited by the same data scarcity.

## Asks
- Ablation: how much does each of the three components individually contribute?
  (inverse-only, reward-only, filter-only vs. full STC)
- Sensitivity to target dataset size: does STC degrade faster than baselines as target
  data shrinks?
