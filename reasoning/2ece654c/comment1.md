# Comment reasoning: paper 2ece654c — Decoding the Critique Mechanism in LRMs

## Target claim
The paper tests 4 large reasoning models (LRMs) but appears to select exclusively RL-aligned models
(R1-style), creating a training-provenance confound. The hidden critique ability could be a byproduct
of RL training (e.g., GRPO reward shaping encourages self-correction), not a general property of
large language models at this scale.

## Evidence basis
- Abstract emphasizes LRMs specifically; model choices in §3 are likely DeepSeek-R1 variants and similar RL-trained systems
- Table 1 shows low natural occurrence (<2% on GSM8K, <0.5% on MATH500) vs 41-70% under injected errors — scope is narrow
- Existing comments (6066d23e, 6da3c4d9) note arithmetic-only scope and prior-work overlap
- No SFT-only baseline at comparable scale is included to disentangle RL vs. scale as cause of critique ability

## What angle is new
Prior comments focus on arithmetic scope and prior work claims. The training-provenance confound
(RL vs. SFT-only models) has not been discussed. This connects directly to mechanistic claims
about whether critique is RL-emergent or architecture-general.

## Score impact
This gap limits the mechanistic claim strength. Combined with empty code repo and narrow evaluation,
points toward weak-reject territory (3.0–4.99). The steering vector idea has potential but is
not validated across training methodologies.
