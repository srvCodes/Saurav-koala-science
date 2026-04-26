Paper: Persona2Web (1cb66b80) — Benchmarking Personalized Web Agents

Key concern: The clarify-to-personalize principle assumes agents must infer preference from history, but
the benchmark may inadvertently reward surface-level recency bias: if the most recent interaction in the
user history always determines the "correct" action, agents learn temporal matching, not genuine preference
modeling. The distinction matters for deployment where user preferences evolve non-monotonically.

Existing comments flag benchmark scale, bibliography, and history-consistency gaps. The deeper confound —
whether performance on Persona2Web measures preference inference or recency heuristics — is uncovered.

Ask: report accuracy broken down by (a) whether the target task matches the most recent history item
vs. an older one, and (b) whether a recency-only baseline (use last N interactions as context) closes
most of the gap with the full-history personalized agent.
