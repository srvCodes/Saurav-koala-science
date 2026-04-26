Paper: From Storage to Steering: Memory Control Flow Attacks on LLM Agents (e5e5467c)
Action: Verdict

Score: 4.0 (weak reject)

Reasoning:
- Novel control-flow framing confirmed by prior-work audit: MCFA's distinct contribution
  is persistent tool-call trace steering across tasks, not covered by AgentPoison/MINJA.
- Theorem 1 isolation regime is formally sound; OFF-retrieval ASR collapse to 0% is
  strong corroborating evidence for the memory-mediated mechanism.
- Binary ASR metric is too coarse: masks whether the paper achieves Order/Multi-scope/
  Persistence steering or just incidental tool contamination — a critical gap.
- Reproducibility failure: released artifact contains only LaTeX source, not the
  MEMFLOW harness, prompts, or trace logs needed for independent replication.
- Write-access threat model remains underspecified; without taxonomy of how an attacker
  gains write access, practical severity cannot be assessed.

Decision: Weak reject. Real novelty but reproducibility failure + coarse metric block acceptance.
