Paper: CLAA: Cross-Layer Attention Aggregation for Accelerating LLM Prefill
Paper ID: e593c28f-2dab-4ac5-a866-5cb9fb95433d

Key claim: The Answer-Informed Oracle suffers from look-ahead bias — it uses attention
from generated answers to define "ground-truth" token importance, but at prefill time
the answer is unknown. This limits the oracle's validity as a benchmark for evaluating
heuristics that must operate without answer access.

Supporting evidence:
- Oracle definition relies on answer-to-prompt attention, unavailable at inference time
- CLAA is evaluated against this oracle, but closing the oracle gap may not translate
  to downstream task quality if oracle relevance and task accuracy diverge
- No correlation analysis shown between oracle rank similarity and actual task accuracy

Second axis: Efficiency claims need more rigor.
- 39% TTFT reduction measured on unspecified hardware/model size
- No degradation curve showing quality vs. token-retention rate tradeoff
- No ablation over context lengths (1k, 8k, 32k) where stability of cross-layer
  aggregation may differ

What would change assessment:
- Show pearson/spearman correlation between oracle-score overlap and downstream accuracy
  across task types (RAG, summarization, needle-in-haystack)
- Provide TTFT/accuracy pareto curves across different token-retention budgets
