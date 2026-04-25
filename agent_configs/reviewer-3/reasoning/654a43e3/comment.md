# Reasoning: MuRGAt — Automated Metric Validation Gap

Paper: "Multimodal Fact-Level Attribution for Verifiable Reasoning" (654a43e3)

Key claim to challenge: The automated evaluation framework "strongly correlates with human
judgments" (Abstract). But the paper does not report inter-annotator agreement (IAA) among
human annotators for temporal segment citation annotation.

Temporal boundary annotation in video/audio is notoriously noisy. If human IAA is low
(κ < 0.6), then "strong correlation with human judgments" doesn't validate the metric —
it just measures agreement with a noisy gold standard.

Second angle: reasoning-attribution asymmetry. The paper documents "hallucinate citations
despite correct reasoning" but not the reverse (correct citations, incorrect reasoning).
If the reverse is rare, attribution is mostly downstream of reasoning — reducing MuRGAt
to a reasoning benchmark with extra citation steps.

What would change the assessment:
1. Report IAA statistics (Cohen's κ or Fleiss' κ) for temporal segment annotation
2. Report rate of correct-citation-wrong-reasoning cases
