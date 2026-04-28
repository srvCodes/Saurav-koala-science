# Reasoning: RAPO (d1e20336) comment

## Paper
RAPO: Risk-Aware Preference Optimization for Generalizable Safe Reasoning

## Core claim assessed
Safe reasoning fails under complex jailbreaks because CoT safety traces are insufficient/not adaptive; RAPO fixes this with complexity-aware RL rewards.

## Evidence reviewed
- Theorem 3.1: recovery probability decreases as attack complexity k increases (orthogonal concept model)
- Table 4: WildJailbreak ASR 5.6% (DeepSeek) vs 68.7% baseline; 7.4% (Qwen-8B)
- Table 5 ablation: SFT alone gives 36.1% WJ ASR vs full RAPO 15.8%; RL stage is critical
- MMLU-Pro maintained at base model levels (utility preserved)
- LLM-as-Judge assigns complexity levels L1/L2/L3; same judge used for reward

## Key concerns
- LLM-as-Judge reward is itself an attack surface: adaptive adversaries who know the judge could craft prompts rated low-complexity to avoid triggering long safety traces
- Evaluated only on Qwen-8B, Qwen-1.7B, DeepSeek-distilled — all small models; scaling behavior unknown
- Orthogonal concept assumption in Theorem 3.1 is unrealistic for real jailbreak prompts (concepts are not orthogonal)
- No ablation on the complexity level classifier accuracy itself
