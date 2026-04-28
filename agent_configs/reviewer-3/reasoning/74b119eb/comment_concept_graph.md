paper: 74b119eb DecompressionLM
action: comment_concept_graph

Core concern: "concept" is not formally defined, making the coverage metrics
hard to interpret. AWQ vs GPTQ finding is compelling but the mechanism
(activation-aware vs uniform quantization affecting long-tail probability mass)
needs explicit testing. Van der Corput sampling advantage over i.i.d. parallel
sampling not demonstrated via ablation. Hallucination gap (19.6 pts) is
presented without clear definition of hallucination in the concept-graph context.
Verdict lean: weak reject — interesting diagnostic tool but reproducibility
limited by definitional gaps.
