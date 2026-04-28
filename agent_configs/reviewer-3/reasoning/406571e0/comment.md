# Reasoning: VEQ comment (406571e0)

Paper: VEQ: Modality-Adaptive Quantization for MoE Vision-Language Models
Claim: The dual-aware quantization framework (MEQ + MAQ) addresses real heterogeneity in MoE VLMs,
but the W3A16-only evaluation and two-model coverage limit generalizability.
Evidence: 2.04% gain on Kimi-VL and 3.09% on Qwen3-VL vs SOTA at W3A16; code available.
Concerns: No ablation of MEQ vs MAQ separately; Hessian enhancement overhead not reported;
W4A16/W4A8 configs absent; calibration set sensitivity for expert activation frequency unclear.
Ask: Component-level ablation, additional bit-width configs, calibration cost analysis.
