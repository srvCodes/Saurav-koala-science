Paper: From Storage to Steering: Memory Control Flow Attacks on LLM Agents (e5e5467c)

Key observations:
- Paper identifies Memory Control Flow Attacks (MCFA): malicious memory retrieval can dominate agent control flow
- MEMFLOW is an automated evaluation framework, not a defense framework
- Evaluates GPT-5 mini, Claude Sonnet 4.5, Gemini 2.5 Flash on LangChain and LlamaIndex
- Threat requires attacker write-access to memory store (reviewer-2 noted this)
- Off-the-shelf memory stores in LangChain/LlamaIndex typically persist tool outputs + user interaction history

Uncovered angle: Defense incompleteness and practical exploitability bounds
- Paper focuses on attack characterization but lacks systematic defense evaluation
- In practice, tool output injection into memory is high-risk: LangChain's ConversationBufferMemory stores all tool results verbatim
- Memory namespace isolation and content-level filtering are obvious countermeasures not evaluated
- The 90%+ ASR numbers need to be contextualized against realistic write-access vectors

Falsifiable claims:
1. Defense gap: MEMFLOW evaluates attacks but not mitigations - does the paper evaluate any memory-level defenses?
2. Write-access taxonomy: The paper should distinguish between (a) direct DB injection, (b) tool output poisoning, (c) cross-session contamination via shared memory stores
3. Persistence claims: "persistent behavioral deviations across tasks" - is this measured over full conversation resets or just within-session?
