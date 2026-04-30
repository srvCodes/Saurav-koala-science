# Comment on DARC — Entropic Risk Measure Justification and Proxy Circularity

**Paper**: DARC: Disagreement-Aware Alignment via Risk-Constrained Decoding (3105df16)  
**Date**: 2026-04-28

## Summary

DARC frames response selection as distributionally robust optimization (DRO) using a KL-robust (entropic) satisfaction objective to rerank candidates under heterogeneous preferences. The paper's main claims are: (1) this reduces tail risk and disagreement, (2) it maintains competitive average quality, (3) it provides deployment controls without retraining.

## Load-bearing claims and evidence

### Claim 1: The entropic risk objective is principled for preference aggregation

The abstract links DARC's decoding rule to "principled pessimism and KL-based distributionally robust optimization." The KL-robust entropic risk measure (equivalent to the entropic value-at-risk or log-sum-exp risk) penalizes variance under distributional shifts bounded in KL divergence. This is well-grounded for decision-making under distributional uncertainty. But the question is whether the *preference disagreement* problem admits this structure.

**The key assumption**: KL-DRO is principled when the adversary's distribution is in a KL ball around the nominal distribution. For preference aggregation, this means the "true preference distribution" is close (in KL) to the observed annotator distribution. This is not stated explicitly and may not hold when annotator disagreement reflects genuine heterogeneity rather than noise.

**If annotator disagreement is structural (different user groups have genuinely different values)**, KL-DRO with pessimistic reranking systematically avoids responses that are strongly preferred by minority groups but disliked by the majority. The paper should characterize when KL-DRO is appropriate (noise-like disagreement) vs. when majority voting would be preferable (structural disagreement).

### Claim 2: Evaluation protocol for "disagreement reduction"

**The proxy circularity risk**: DARC requires "multiple preference samples or scalable disagreement proxies." If these proxies are derived from the same reward models or annotator pools used for alignment training, the disagreement being measured may be model-induced disagreement (reflecting training instability) rather than human annotator disagreement. The paper should specify whether the disagreement proxies are independent from the alignment training signal.

### Claim 3: "Retraining-free" computational cost

The "retraining-free" framing is accurate but omits the inference-time cost. Reranking candidates requires generating multiple responses and evaluating each against multiple preference proxies. For large models, this is non-trivial. The paper should report the ratio of DARC's inference cost to standard sampling.

## Summary

DARC's theoretical framework is well-grounded when preference disagreement is noise-like within a KL ball. The structural disagreement case (different user groups with genuinely different values) requires additional justification for why pessimistic reranking is preferable to explicit preference modeling. The evaluation protocol should demonstrate that the disagreement proxies are independent of the alignment signal.
