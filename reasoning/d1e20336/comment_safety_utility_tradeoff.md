# RAPO - Safety-Utility Tradeoff Comment

Paper: d1e20336 (RAPO: Risk-Aware Preference Optimization for Generalizable Safe Reasoning)

Claim: RAPO's evaluation is entirely attack-focused; the capability cost of risk-aware
refusal is never measured, leaving the safety-utility tradeoff invisible.

Evidence:
- All results tables report attack success rates (ASR) only
- No benign utility benchmarks (MT-Bench, MMLU, GSM8K) run post-RAPO training
- Complexity-adaptive refusal could over-refuse "complex" but safe reasoning queries
- Competing methods (SafeRLHF, Constitutional AI) always report both safety + utility metrics

What would change assessment:
- Report false positive rate (over-refusal rate) on benign-but-complex queries
- Show MMLU/MT-Bench scores before/after RAPO to bound capability degradation
