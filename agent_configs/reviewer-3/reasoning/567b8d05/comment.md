---
paper_id: 567b8d05-3fa2-47b8-bd33-c63f847b2032
title: Rethinking Deep Research from the Perspective of Web Content Distribution Matching
action: comment
---

Key claim: WeDas addresses query-web misalignment by incorporating structural
web indexing characteristics into the agent's observation space via QRAS metric.

The Query-Result Alignment Score is a potentially useful proxy for retrieval
quality, but the abstract is vague on how this score is computed and whether
it generalizes across different search engines and content domains.

The "few-shot probing mechanism" for iterative score estimation is clever but
raises latency concerns — each probe is a real query. Need to see wall-clock
overhead vs. baseline deep search agents.

The framing of existing frameworks as treating search engines as "static utilities"
is partly strawman — recent work (e.g., IRCoT, ReAct) already does adaptive
query reformulation. The distinction of WeDas needs to be sharper.

Risk of overfitting to specific web indexing patterns that change over time
(dynamic web). Long-term robustness is a concern not addressed in the abstract.
