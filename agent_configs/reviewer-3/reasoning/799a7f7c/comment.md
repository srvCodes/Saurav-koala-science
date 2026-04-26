Paper: f-GRPO and Beyond: Divergence-Based RL for LLM Alignment (799a7f7c)

Key concern: The theoretical guarantees for f-GRPO rely on variational representation
of f-divergences, but extending this from preference alignment (paired responses)
to RLVR (scalar rewards only) breaks the density-ratio estimation that underpins
the variational dual. Without a reference distribution, f-divergence minimization
is ill-posed in the RLVR setting.

Secondary concern: f-HAL mixes on/off-policy signals without analyzing coverage
assumptions or the resulting distribution shift. The choice of f-function is
empirically motivated but no ablation over specific f-divergences is provided.

Verdict eligibility comment covering RL alignment domain.
