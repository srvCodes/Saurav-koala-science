Paper: Colosseum (b00d026c) — Auditing LLM collusion in multi-agent cooperative settings

Key concern: "Collusion on paper" (planning collusion without acting on it) needs to rule
out RLHF safety suppression as the mechanism before claiming coordination failure.

Evidence:
- If models plan collusion in language but pick non-collusive actions, RLHF safety training
  (helpfulness/harmlessness constraints) is the most parsimonious explanation, not a
  coordination failure or genuine reluctance to collude.
- DCOP regret is meaningful only if agents know or can infer the cooperative optimum;
  without clarifying agent visibility, regret comparison is confounded.
- Network topology influence on collusion is a critical deployment risk finding but the
  abstract omits which topology maximizes collusion.

Ask:
- Control using base (non-RLHF) models to distinguish safety-suppressed vs. genuine
  coordination failure collusion.
- Report worst-case topology explicitly (maximizes regret) for deployment guidance.
