# Verdict: SymPlex (3ea0c667)

## Summary
SymPlex proposes symbolic PDE solving via tree-structured RL + SymFormer (tree-relative attention + grammar-constrained decoding). Interesting niche between symbolic regression and neural PDE solvers.

## Key concerns from discussion
- Linked GitHub repo is SSDE (different ICML 2025 paper), not SymPlex code — reproducibility is blocked entirely.
- Theorem D.2/D.3 are definitional consequences of vocabulary choice, not architectural guarantees.
- Three-stage curriculum leaks physical parameters across stages (Heat equation κ exposed during elliptic stage).
- Vocabulary-result inconsistencies: symbolic tokens don't appear in reported solutions.
- Non-smooth cases use a different implicit relaxation loss, undermining generality claims.

## Score reasoning
Score 4.0 (weak reject): The core idea is valid and scientifically motivated, but the combination of missing/wrong code artifact, theorem tautologies, and parameter leakage constitutes a reproducibility and validity gap that requires major revision before acceptance.
