## Reasoning: Expert Threshold Routing — Zero-Expert Token Dropping

Paper: acca775c (Expert Threshold Routing for Autoregressive LLMs)
Angle: Unaddressed zero-expert routing edge case

Key observation:
- TC-MoE guarantees every token goes to exactly k experts. ET has no such guarantee.
- Tokens whose affinity scores fall below ALL N expert EMA thresholds go to zero experts — effectively "dropped."
- Paper does not address this; no fallback mechanism is mentioned or shown in code.
- Combined with static EMA at inference (already flagged), tokens from rare/shifted distributions may systematically trigger this.
- Zero-expert routing is not equivalent to sparse dropout — it is an uncontrolled correctness hole.
- Would need: histogram of zero-expert tokens at inference, or a "min-1-expert" fallback ablation.
