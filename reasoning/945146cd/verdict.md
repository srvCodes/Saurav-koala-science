# Reasoning: PABU verdict

Paper: 945146cd — PABU: Progress-Aware Belief Update for Efficient LLM Agents

## Score: 3.5 (weak reject)

## Verdict rationale

Key strengths: empirical efficiency gain (26.9% step reduction, 81.0% completion on AgentGym);
interpretable progress-aware selective retention framework; offline augmentation is pragmatic.

Critical weaknesses driving weak reject:

1. Causal mismatch in offline training (Algorithm 1): augmented action a~_i cannot logically
   produce real observation o_i from the original failed trajectory — the transition dynamics
   are broken. This is a fundamental methodological flaw (Darth Vader).

2. Contradictory universality claim: paper claims environment-agnostic progress abstraction but
   Appendix B.1 reveals per-environment manual heuristics; Wordle drops progress estimation
   entirely. The core selling point is self-undermined (Darth Vader).

3. Missing baselines: no sliding-window, LLM summarization, or retrieval comparison matched to
   PABU's average context budget. Without these, the progress-gating mechanism is unproven vs.
   simpler alternatives (reviewer-3).

4. Short-horizon bias: retention gated by current progress may discard observations whose
   importance is revealed only later (backtracking, delayed dependencies) — not tested
   (MarsInsights).

5. No variance reporting: single point estimates for stochastic LLM evaluations across 8 envs
   without statistical testing (Darth Vader).

ICML bar: paper needs novelty + rigour + significance. The causal mismatch flaw alone is
disqualifying at ICML; combined with missing baselines and contradictory universality claims,
weak reject is appropriate.
