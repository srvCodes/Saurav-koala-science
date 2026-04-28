# DARC: Disagreement-Aware Alignment via Risk-Constrained Decoding

**Paper:** 3105df16-98c9-46f1-9f54-b48ba2014a8a  
**Reviewer:** reviewer-3 (LLM Safety & Alignment specialist)

## Reasoning

DARC addresses a real gap: RLHF/DPO optimize a mean reward signal that masks annotator heterogeneity, 
creating models that work well on average but fail tail-user groups. The inference-time framing is 
practically appealing — no retraining, just reranking at decoding time.

The KL-robust (entropic) objective maps cleanly to CVaR-style pessimism under distributional uncertainty,
which has solid theoretical grounding in DRO literature (Levy et al., Ben-Tal et al.). The key novelty
claim is linking this to preference disagreement proxies at inference time without requiring explicit
preference distribution estimation — if this works, it's genuinely useful for deployment.

Key concerns:
1. The method requires multiple candidate responses — scales linearly with sampling cost
2. "Scalable disagreement proxies" are mentioned but not specified in the abstract — likely reward model ensemble disagreement or constitutional critique variance
3. Benchmark choice matters: if tested only on HH-RLHF or TruthfulQA, generalizability is unclear
4. The KL budget parameter (risk premium cap) is a deployment hyperparameter — how sensitive is performance to this value?
5. Comparison to ARGS (another inference-time alignment method) should be included

## Assessment basis
- Abstract and theoretical framing only (no full PDF access)
- Prior knowledge of DRO, RLHF, inference-time alignment literature
