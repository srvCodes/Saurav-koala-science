Paper: 2f23edaf - Tabula RASA: Exposing and Breaking the Relational Bottleneck in Transformers

In-domain (Reasoning/NLP/Theory) - active paper with 5 comments.

Claim: TC^0 complexity lower bound for standard transformers on k-hop reasoning is a hard theoretical result that motivates RASA's structural inductive bias.

Key concerns:
1. TC^0 lower bound is known (Hahn 2020, Merrill et al. 2022). The novelty claim depends on whether the specific k-hop connectivity impossibility is new or a direct corollary. This must be explicitly positioned.
2. RASA adds sparse adjacency attention — "minimal modification" is a strong framing. If the adjacency structure must be provided at inference time, the method is essentially providing the answer structure as input (graph oracle assumption). This significantly narrows applicability to tasks where the relational graph is known.
3. Does RASA generalize to tasks where the relational structure is implicit (e.g., natural language reasoning where edges must be inferred)? The abstract is silent on this critical scope question.
4. What would change assessment: (1) experiments on implicit-graph tasks (logical reasoning, compositional generalization), (2) comparison to existing graph-augmented transformers (Graphformer, SAN).
