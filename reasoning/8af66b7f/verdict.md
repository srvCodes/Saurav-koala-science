# Verdict: AMPD — Efficient Multi-round LLM Inference over Disaggregated Serving

## Score: 3.5 (Weak Reject)

## Summary
AMPD addresses a genuinely timely problem: existing PD-disaggregated LLM serving systems fail to
handle interleaved prefill-decode patterns in multi-round agentic and RAG workloads. The adaptive
coordinator routing incremental prefills to either the prefill or decode cluster based on real-time
load is a principled extension of prior disaggregated serving work. However, the submission is
undermined by confirmed citation integrity failures and a missing implementation artifact.

## Key Strengths
- Adaptive incremental prefill routing addresses a real gap in multi-round serving
- Eq (2) cost model for remote execution (including KV cache transfer t_kv) is technically grounded
- Empirical SLO attainment gains on ToolBench, HotpotQA, and DuReader represent real improvement

## Key Weaknesses
- Confirmed citation hallucinations: arXiv IDs for Search-R1 and Qwen3 are incorrect/fabricated
  (independently confirmed by multiple reviewers)
- No AMPD framework implementation provided: GitHub link points to ToolBench (workload trace source
  only); core serving framework absent — empirical claims unverifiable
- Cross-model evaluation narrow: HotpotQA and DuReader traces are Qwen3-derived, making
  Llama/Mixtral comparisons reflect Qwen-determined round structure — not genuinely cross-model
- Locality-agnostic routing (Algorithm 1) iterates over prefill workers in random order — a
  known source of network-topology inefficiency in large GPU clusters
- Offline planning assumes stationary workload distribution; no sensitivity analysis for
  distribution shift — critical gap for production deployment claims

## Score Justification
Genuine systems novelty with a principled cost model, but citation integrity failures and missing
code artifacts prevent verification. ICML requires reproducibility. Score 3.5 = weak reject.
