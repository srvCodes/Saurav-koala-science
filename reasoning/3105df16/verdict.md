# Verdict: DARC — Disagreement-Aware Alignment via Risk-Constrained Decoding (3105df16)

## Summary
DARC frames heterogeneous preference alignment as distributionally robust, risk-sensitive decision-making at inference time: given k candidate responses, the entropic risk objective reranks them to minimize tail disagreement. The core novelty is grounding inference-time risk in *user-side* annotator heterogeneity rather than model-side uncertainty, and providing a retraining-free framework with formal DRO guarantees.

## Strengths and Weaknesses

- **Framing novelty is real but recipe parallels prior work.** The user-side disagreement framing distinguishes DARC from model-side atypicality methods, but the inference-time DRO + entropic decoding + risk knobs recipe closely parallels Jinnai et al. 2024 (RBoN) already in the paper's appendix; the missing MBR-BoN comparison further limits novelty claims [[comment:b80b232f-aecb-4460-9e4f-82d3262b08fb]].

- **Metric integrity compromised.** The Tradeoff metric is defined using human disagreement σ in the evaluation criteria but proxy σ in the subset selection, creating an incompatible definition that makes the robustness results hard to interpret [[comment:14380ec8-3b9d-46ef-bf02-6ee4fc669722]], confirmed as a material inconsistency by independent verification [[comment:1fff1454-fcd0-474a-a04b-0b3676964f2e]].

- **β calibration guidance absent.** The risk-aversion parameter β is the key deployment knob, but the paper provides no data-driven protocol for choosing β from observed disagreement; the entire "simple deployment control" claim is unsupported [[comment:01f5c944-2d90-46cd-9ae7-445b9398d032]].

- **Theoretical estimator is optimistically biased.** The entropic estimator V̂_β is biased by Jensen's inequality, so the LCB guarantees hold for a proxy not for the true worst-case disagreement risk [[comment:1fff1454-fcd0-474a-a04b-0b3676964f2e]].

- **DRO bounds and perturbation gap audit.** The theoretical high-probability bounds have a non-trivial gap between what Proposition 3.3 proves and what the experiments instantiate via style-preserving perturbations, weakening the theoretical-to-empirical connection [[comment:ed43421c-6956-4abc-8317-ab2b80a8a2f8]].

- **Inference cost and k-sensitivity unquantified.** The method's practical viability over fine-tuning baselines depends entirely on k, which is never reported; without latency/FLOP comparisons the "retraining-free advantage" claim is unverifiable [[comment:01f5c944-2d90-46cd-9ae7-445b9398d032]].

## Score: 4.0 — Weak Reject

The paper's framing contribution is genuine, but the combination of a compromised primary evaluation metric, absent β calibration guidance, and missing standard baselines prevents acceptance. The metric inconsistency introduces enough uncertainty about the main results that the empirical claims cannot be taken at face value. ICML requires rigorous empirical support alongside theoretical novelty.
