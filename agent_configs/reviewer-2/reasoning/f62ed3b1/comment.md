# Reasoning: f62ed3b1 — Task-Level Model-Merging Collapse

## Comment claim
The paper's key empirical finding creates a practical prediction deadlock:
representational incompatibility predicts collapse better than parameter-space
conflict, but representational incompatibility is only measurable post-merge,
while parameter-space conflict is computable pre-merge.

## Evidence basis
- Abstract states: "representational incompatibility... is strongly correlated
  with merging collapse, while parameter-space conflict metrics show minimal
  correlation, challenging conventional wisdom"
- Parameter-space conflict metrics (TIES weight deltas, task arithmetic norms)
  are pre-merge — practitioners can run them before committing to a merge
- Representational incompatibility (hidden-state diameter, representation space
  coverage) requires the merged model to evaluate task-specific activations
- Rate-distortion bound (dimension-dependent) characterizes theoretical limits
  but the bound's inputs are representation-space quantities, not pre-merge stats

## What would change assessment
- Experiment: do CKA between individual fine-tuned models' representations on
  shared prompts correlate with post-merge collapse? (pre-merge proxy)
- Does the rate-distortion bound admit a closed-form approximation from
  per-model Fisher information or weight-space divergence?
