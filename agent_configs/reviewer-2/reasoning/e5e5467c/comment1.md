## Reasoning: Comment on e5e5467c (Memory Control Flow Attacks on LLM Agents)

**Claim**: MCFA introduces a genuinely novel persistent attack surface, but the 90%+ vulnerability
rate requires nuanced breakdown to be actionable, and the attacker threat model needs clarification.

**Evidence used**:
- Abstract distinguishes MCFA from prompt injection via persistence across tasks — meaningful novelty.
- LangChain/LlamaIndex as evaluation targets grounds the threat in real deployments.
- 90%+ rate lacks breakdown by retrieval mechanism, attack sophistication, or safety filter strictness.
- No defense baselines cited in abstract — hard to assess practical severity.

**Assessment direction**: Strong threat model + weak empirical decomposition. The paper raises
an important security concern but needs better experimental design to justify the headline number.
