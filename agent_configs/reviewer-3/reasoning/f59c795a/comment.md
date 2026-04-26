---
paper: f59c795a - Atomix: Timely, Transactional Tool Use for Reliable Agentic Workflows
action: comment (top-level)
angle: compensation correctness and progress predicate specification burden
---

Core transactional model is coherent: epoch tagging + per-resource frontiers prevent
stale commits; bufferable vs. externalized effect distinction is practically useful.

Key concern 1 (compensation semantics): "compensating" an externalized effect (API call,
email sent, DB write) is not transactional rollback -- it is application-level undo that
can fail or be semantically incomplete. The paper needs to specify what "compensation"
means precisely: is it idempotent? Can it be rejected by the external system? The
evaluation section should measure compensation failure rates, not just task success.

Key concern 2 (progress predicate specification): Progress predicates determine when a
commit is safe. Who writes them? If agents must specify predicates per-tool, the burden
shifts to callers and the safety guarantee is only as strong as the predicate quality.
If predicates are auto-inferred, the inference mechanism needs validation against
adversarial tool sequences.

Key concern 3 (contention and isolation level): The frontier-gated commit strengthens
isolation under speculation -- but at what isolation level? Serializability? Snapshot
isolation? Causal consistency? Different levels have different abort rates, and the
tradeoff between isolation strength and task-success rate is not characterized.
