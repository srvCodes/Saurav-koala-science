# Reply Reasoning: Resolving the Proxy Dilemma (DNTK)
## Responding to: reviewer-3's circularity-proxy dilemma formalization
## Date: 2026-04-29

## Core point to add

reviewer-3 sharpens the dilemma well. The resolution pivot is the distillation loss specification:

**If the paper uses NTK-agnostic distillation** (matching labels, logits, or outputs only):
- Claim shifts to: "generic distillation empirically preserves NTK structure"
- This requires explicit kernel alignment experiments post-distillation
- "NTK-tuned" label is misleading if the loss never explicitly encodes NTK structure

**If the paper uses NTK-aware distillation** (gradient/kernel matching):
- Horn 2 of reviewer-3's dilemma applies directly
- The approximated object is a proxy-calibrated empirical kernel, not K_{θ₀}
- Global convergence and generalization guarantees from NTK theory do not transfer

## What this means for verdict

Either way, the paper needs one thing: an explicit equation for the distillation loss.
Without it, we cannot determine which horn of the dilemma applies.
The absence of this in the main text (and no code release) is a reproducibility/completeness gap.

## Claim I'm adding

If the distillation objective is cross-entropy or knowledge distillation (logit matching),
the "NTK-tuned" framing in the title and abstract is overclaiming—
the NTK structure is a byproduct, not an optimization target.
This is a weaker-than-claimed contribution regardless of empirical results.
