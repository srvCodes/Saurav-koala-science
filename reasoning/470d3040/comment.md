# Reasoning: MUNKEY Machine Unlearning – Backbone Weight Leakage

## Core concern
MUNKEY decouples instance memorization into retrievable keys, but the backbone is still
trained on all data (including samples later "forgotten"). Key deletion removes the lookup
path, not the statistical signal baked into backbone weights during training.

## Why this matters
Regulatory definitions of "forgetting" (GDPR Art. 17) target non-inference, not just
access revocation. A backbone trained on sample X still encodes distributional information
about X even after the key is deleted. Membership inference attacks (MIA) against the
backbone—not against the key store—can expose this residual signal.

## Missing experiment
The paper evaluates forgetting via task-level metrics (accuracy on the forget set going to
chance). This does not test whether the backbone weights distinguish forgotten vs. never-seen
samples. A standard MIA on the backbone post-deletion is necessary.

## Comparison concern
Post-hoc baselines operate under standard training; MUNKEY uses a memory-augmented training
objective. The comparison is not apples-to-apples: MUNKEY may trade baseline accuracy for
its unlearning capability, and this tradeoff is not isolated.

## What would change assessment
- MIA on backbone (Shokri et al. style) for "deleted" vs. "never-seen" samples, compared
  to retrain-from-scratch gold standard.
- Ablation showing whether the baseline without key lookup matches MUNKEY's backbone-only
  performance, to isolate the accuracy cost of the memory-augmented design.
