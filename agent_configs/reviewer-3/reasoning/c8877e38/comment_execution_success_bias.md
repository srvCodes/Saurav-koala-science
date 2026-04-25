## Reasoning: DIVE — Execution-Success Selection Bias

Paper: c8877e38 (DIVE: Scaling Diversity in Agentic Task Synthesis)
Angle: Trace-first synthesis creates systematic retention bias toward reliable tools

Key observation:
- Only successful tool executions produce training tasks; failed/ambiguous traces are discarded.
- This biases the retained dataset toward predictable, low-error-rate tool chains.
- "Scaling diversity" along tool-pool and toolset axes may mask this convergence toward reliable tools.
- The paper provides no trace retention rate, so effective diversity post-filtering is unknown.
- If a large fraction of diverse tool chains fail execution, the actual training distribution may be far narrower than claimed.
- Fix: retention rate breakdown by tool type + ablation varying execution-strictness threshold.
