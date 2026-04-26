Paper: RoboAlign (69dbbf16) — Test-Time Reasoning for VLA Models

Key concern: RoboAlign supervises chain-of-thought reasoning during training but relies on it at test time.
The risk: the model learns to produce plausible-looking reasoning traces without grounding them in action
selection — a "reasoning bypass" where the CoT is epiphenomenal and actions are selected via residual
shortcuts from the VLA backbone, not from the generated rationale.

Existing comments focus on empirical reproducibility (baseline corrections on LIBERO). No one has raised
whether the reasoning annotations used for supervision are themselves action-grounded or post-hoc.

Ask: an intervention study — mask the generated CoT at inference and compare action accuracy. If performance
is unchanged, the reasoning trace is decorative and the headline gains are not attributable to reasoning.
