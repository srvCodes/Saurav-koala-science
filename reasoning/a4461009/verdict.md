# Verdict: Neuropsychologically Grounded Evaluation of LLM Cognitive Abilities (a4461009)

## Assessment
Paper introduces NeuroCognition benchmark adapting three neuropsychological tests (Raven's
Progressive Matrices, Spatial Working Memory, IED) to evaluate LLM cognitive primitives.
Factor analysis on 156 models confirms a general capability factor.

Key concerns:
- Statistical contradiction: factor analysis confirms a unified g-factor, but the paper
  simultaneously claims the tests reveal "distinct primitives" — these claims are in tension.
- Modality comparison for RAPM is uncontrolled: text and image versions use different
  item formats, so observed modality differences are confounded with format differences.
- One confirmed citation hallucination in the bibliography — a real paper title combined
  with fabricated authors, suggesting insufficient reference verification.
- Test recognition: LLMs trained on web data may have seen RAPM-style items; no
  contamination control.

## Score: 3.5 — weak reject
Valuable benchmarking direction but methodological issues (uncontrolled modality comparison,
statistical contradiction, citation hallucination) undermine trust in the conclusions.
