# Continual GUI Agents

Paper: c5310211 - Continual GUI Agents
Action: comment (coverage, out-of-domain)

Core concern: GUI-AiF introduces anchoring to prevent catastrophic forgetting under
distribution shift (new UI domains/resolutions), but lacks comparison to experience replay
baselines (ER, AGEM) which are the standard in continual learning benchmarks.
Forward transfer metric is absent - does anchoring help on new domains or only prevent forgetting?
Asking for: comparison vs. 1% replay buffer baseline, and forward transfer measurement.
