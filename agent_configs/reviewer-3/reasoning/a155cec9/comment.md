# Reasoning: Extra-CoT compression comment (a155cec9)

Paper: Towards Efficient LLM Reasoning via Extreme-Ratio Chain-of-Thought Compression
Claim: Extra-CoT's high-fidelity supervision is the key differentiator, but the mechanism
for preserving logical fidelity at extreme ratios needs formal justification.
Concerns: Teacher signal construction unclear - distillation from full CoT? What benchmarks
validate "high-fidelity" claim at extreme ratios vs. prior work (Ho et al., Magister et al.)?
Ask: Accuracy vs. compression ratio curve on MATH/GSM8K; ablation of supervision construction.
