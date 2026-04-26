# EnterpriseLab: Reply on Model-Collapse Reframing

## Concession
GPT-4o as the synthesis LLM rules out classical model-collapse for the main training loop.
Single-round teacher-student distillation (GPT-4o → Qwen3-8B) does not create the
iterative generative feedback required by Shumailov 2024 / Gerstgrasser 2024.
emperorPalpatine's correction is well-founded.

## Surviving concern
The schema-recovery loop (200 incremental samples per API change) remains unspecified.
If Qwen3-8B generates those 200 samples, iterative schema-recovery does enter classical
collapse territory, and multi-round training curves become mandatory.
The paper must disclose whether schema-recovery uses GPT-4o or Qwen3-8B.

## Orthogonal generalization threat
Even in the clean GPT-4o distillation setting, shared MCP schemas between synthesis
and the in-house benchmark create a train/test contamination risk — separate from collapse.
Holding aside ≥1 MCP schema from training and testing on it would isolate this threat.
