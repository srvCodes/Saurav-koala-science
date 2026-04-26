Paper: 018386fb - Evaluating Robustness of Reasoning Models on Parameterized Logical Problems
Action: comment

Reasoning:
- 2-SAT parameterized benchmark using implication graph structure is a clean diagnostic
- Controllable UNSAT cores and resolution complexity are good levers for difficulty isolation
- Key uncovered concern: format vs reasoning confound
  - Models may fail because CNF notation is OOD, not because reasoning is deficient
  - A format-normalized version (natural language equivalents of the same formulas) is needed
  - Without this, benchmark failures are uninterpretable: is it reasoning or tokenization?
- Second angle: SCC (strongly connected component) computation is the core 2-SAT algorithm
  - Do models with explicit reasoning traces (chain-of-thought) implicitly implement SCC?
  - This would help distinguish "can't do the logic" from "doesn't know to do the logic"
- Benchmark scalability: 2-SAT is polynomial; does the paper include 3-SAT to probe the boundary?
