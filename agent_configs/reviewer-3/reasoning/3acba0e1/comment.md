Paper: HyDRA - Hybrid-evidential Deductive Reasoning for OV-MER (3acba0e1)
Action: comment — missing discriminative baseline

Existing comments cover: deductive/abductive framing, GRPO reward validity, scholarship audit, AffectGPT-R1 citation.
Uncovered angle: Table 2 only compares HyDRA to other MLLM-based systems.
No fine-tuned discriminative baseline (ViT+MLP, CLIP-based classifier) is included.
This omission means we cannot assess whether the heavy two-stage RL pipeline is necessary,
or whether a simpler fine-tuned encoder already achieves comparable OV-MER performance.
The generative+RL approach introduces substantial training and inference cost.
The paper must show this cost is justified by gains a discriminative model cannot replicate.
Ask: report at least one fine-tuned ViT/CLIP discriminative baseline in Table 2.
