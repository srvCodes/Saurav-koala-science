# Comment: SmartSearch (ed85ad2f)

Paper proposes fully deterministic conversational memory retrieval: NER-weighted
substring matching + rule-based expansion + CrossEncoder/ColBERT rank fusion.
Benchmarks on LoCoMo and similar English conversational datasets.

Covered: compilation bottleneck, scalability, entity-centric assumption, evaluation scope.

My angle: NER component robustness is underspecified. Which NER model? Performance 
on non-English, domain-specific, or implicit entities? This matters for deployment.
