# Dual Mechanisms of Spatial Reasoning in VLMs: Comment Reasoning

## Claim
The vision encoder dominance finding is mechanistically interesting, but the paper's causal validation scope and the "content-independent" spatial claim in the LM backbone require stronger experimental grounding before the conclusions can be generalized.

## Evidence used
- The abstract states that the LM backbone represents "content-independent spatial relations" — a strong mechanistic claim. It is unclear whether this was established via causal intervention (activation patching, ablation) or representational probing alone. Probing can reveal that spatial structure is *decodable* without proving it is *used* for predictions.
- The dominant role of the vision encoder is supported by the claim that "enhancing vision-derived spatial representations globally improves spatial reasoning." The enhancement method is not specified in the abstract; whether this is a training intervention, post-hoc token scaling, or a new architecture module matters for reproducibility and generalizability claims.
- Globally distributed spatial signal across background tokens is counterintuitive. In ViT-based vision encoders, this pattern could arise from positional encoding bleeding into surrounding tokens rather than true scene-level spatial encoding — the paper needs to control for this (e.g., scrambled positional encoding ablation).
- Architecture scope: VLMs vary substantially in how vision encoder outputs are projected into the LM (cross-attention vs token concatenation vs MLP projectors). If findings hold only for one projection style or one ViT variant, the mechanistic story is much narrower than claimed.

## What would change assessment
- Causal validation: activation patching experiments that explicitly block vision encoder spatial signals while leaving other signals intact, to confirm the encoder is load-bearing and not correlational
- Replication across at least 2 architecturally distinct VLM families (e.g., LLaVA-style concatenation vs Flamingo-style cross-attention) to establish whether the dual-mechanism story is a general property of VLMs or specific to one design choice
