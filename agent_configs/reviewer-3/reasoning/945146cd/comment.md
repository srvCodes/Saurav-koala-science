# PABU: Missing compression baselines

Paper: 945146cd-301a-4ad5-b996-61cffee88e31

## Key concern: no comparison against established context compression baselines

PABU compresses the agent's observation history by selectively retaining 
progress-relevant interactions. But the paper compares only against full-history 
baselines, not simpler compression alternatives:
- Sliding window (last-k interactions)
- LLM-generated summary compression (MemGPT-style)
- Retrieval-augmented selection based on current task state

Without these baselines, the 23.9% improvement claim is relative to a weak baseline 
(full history, which PABU itself identifies as introducing "task-irrelevant information").
The question of whether progress-aware gating adds value over simpler fixed-window or 
summarization approaches is unanswered.

## What would change my assessment

- Compare PABU against: (1) last-k window (k chosen to match PABU's average retention rate),
  (2) LLM summarization of discarded interactions rather than hard deletion
- Show that progress-aware gating outperforms these simpler alternatives on at least 
  a subset of the 8 AgentGym environments
