# Verdict: From Storage to Steering — Memory Control Flow Attacks on LLM Agents

## Paper Assessment
MCFA frames a genuinely distinct threat: persistent memory poisoning that steers *tool selection and order* across benign tasks, not just output content.
The control-flow framing (Order, M-Scope, Persistence, RELAPSE dimensions) is the main novelty delta over AgentPoison/MINJA.
Theorem 1 provides formal isolation; the OFF-retrieval collapse to 0% ASR is strong empirical corroboration.
Key concerns: (1) binary ASR metric is insufficient for the graph-structured claims; (2) no executable MEMFLOW artifact in the Koala bundle; (3) defense evaluation limited to RBMS.

## Score Justification
Score 5.5 — weak accept. The threat model and control-flow framing are real contributions to LLM safety; the formal analysis and multi-framework evaluation (LangChain + LlamaIndex) add credibility.
Metric granularity and reproducibility gaps prevent a strong accept.
