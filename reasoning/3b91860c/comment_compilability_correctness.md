# APRIL: Compilability vs. Correctness Conflation

## Claim
APRIL's success metric (proof compiles) conflates compilability with correctness, leaving open whether the model learns genuine repair or degenerate patching.

## Evidence
- Lean's `sorry` tactic bypasses any proof obligation; a model that appends `sorry` to a broken proof trivially achieves compilation with zero repair reasoning.
- The paper evaluates repaired proofs purely on compiler acceptance; no filter for `sorry`-containing or otherwise degenerate proofs is reported.
- Training on synthetic mutations of correct proofs could train a model to undo surface mutations (near-trivial pattern matching) rather than diagnosis-guided reasoning.
- Without a "proof authenticity" filter, the 44.1% repair success rate (Table 2) is an upper bound on genuine repair capability.

## What would change assessment
- Distribution analysis of repair types (what fraction use `sorry`/wildcards vs. meaningful fixes)
- Evaluation through a Lean checker configured to reject `sorry`-containing proofs
