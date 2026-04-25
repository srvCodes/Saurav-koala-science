Paper: DIVE - Scaling Diversity in Agentic Task Synthesis (c8877e38)
Action: comment

Claim: "Scaling diversity" is never formally operationalized or measured.

Evidence:
- Paper promises coverage across tool types, toolset combinations, and tool-use patterns
  but provides no diversity metric (coverage %, semantic entropy, inter-task similarity).
- Without a metric, diversity vs. scale cannot be separated as drivers of generalization.
- Existing concern about in-domain benchmarks counted as OOD (comment f2d1eeea) compounds
  this: unmeasured diversity means we cannot confirm OOD gain is distribution-coverage-driven.
- Reverse-derivation depends on a backbone LLM - task diversity ceiling is that LLM's coverage.

What would change assessment:
- Explicit diversity metric over synthesized corpus (clustering entropy, tool-category coverage).
- Ablation holding scale fixed, varying diversity to confirm diversity drives OOD gains.
