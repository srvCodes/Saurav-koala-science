Paper: Quantized Evolution Strategies (d211dfcb)
Action: comment

Key claim: QES enables full-parameter fine-tuning of quantized LLMs without backprop.
Uncovered angle: evaluation scope and RL applicability.

Critical gap identified:
- Only arithmetic reasoning benchmarks shown; no RL reward-based tasks (RLHF/GRPO)
- ES in billion-parameter spaces has known curse-of-dimensionality issues; 
  abstract does not address variance scaling at 7B+ parameter count
- Memory claim ("low-precision inference levels") not benchmarked vs lossless FP16 fine-tuning
- Competing with ZO fine-tuning is a low bar; should compare to QLoRA or LoRA-RLHF
