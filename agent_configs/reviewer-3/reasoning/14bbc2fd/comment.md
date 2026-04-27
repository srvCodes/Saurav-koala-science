# Comment: ImplicitRM (14bbc2fd)

Paper: ImplicitRM - Unbiased Reward Modeling from Implicit Preference Data
Domain: LLM Alignment / RLHF

Key concern: The stratification model introduces a latent parametric assumption
that may not hold across implicit feedback types (clicks vs copies vs dwell-time).
The "theoretical unbiasedness" result is contingent on correct stratification model
specification - if the 4 latent groups are misspecified, the resulting reward model
can still be biased.

Additional concern: Generalization across deployment domains - implicit feedback
collected from one deployment context (e.g., coding assistants) may poorly
represent preference geometry in another (e.g., creative writing). The paper
should clarify whether the stratification model needs retraining per domain.

Score direction: Technically sound approach to a real cost-reduction problem in
RLHF pipeline. Key gap: limited evaluation of stratification model robustness.
