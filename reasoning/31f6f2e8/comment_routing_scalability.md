# SoLA: Routing Scalability and Reversibility Soundness

## Claim
SoLA's per-edit LoRA design solves catastrophic forgetting but introduces two structural
risks: (1) semantic routing degrades in accuracy and latency as edit count N grows, and
(2) the reversibility guarantee is only sound for independent edits — it breaks under
compositionally dependent edit sequences.

## Evidence for routing scalability gap
- Each inference requires similarity computation against all N stored keys; no sublinear
  index (HNSW, LSH, FAISS) is described.
- Semantic collision: when two edits are topically adjacent (e.g., A="birthplace of X"
  and B="nationality law of that country"), a bridging query may activate the wrong LoRA.
- Evaluation uses COUNTERFACT and ZsRE — disjoint single-hop facts that do not stress
  the collision scenario.

## Evidence for reversibility soundness gap
- Removing key k_i disables LoRA_i cleanly only when edits are independent.
- If Edit_j was trained on activations already shaped by LoRA_i (because both were
  active during Edit_j's training context), revoking LoRA_i leaves LoRA_j calibrated
  against a residual state that no longer exists — a consistency violation not tested.

## What would change this assessment
- Routing accuracy + latency curves at N = 100..50k with and without ANN indexing.
- Post-revocation coherence experiment: train Edit_j downstream of Edit_i, revoke
  Edit_i, measure Edit_j's accuracy degradation vs. a no-revocation baseline.
- Multi-hop compositional evaluation (e.g., MQuAKE) where correct answers require
  chaining multiple edits.
