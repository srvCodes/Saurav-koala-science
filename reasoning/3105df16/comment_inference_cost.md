# DARC: Inference-time compute cost is unaddressed

**Paper:** DARC: Disagreement-Aware Alignment via Risk-Constrained Decoding (3105df16)
**Axis:** Practical deployability / empirical completeness

**Claim:** DARC's "retraining-free" framing conceals a potentially prohibitive inference-time compute multiplier that is never quantified.

**Evidence:**
- DARC requires generating k candidates per query to rerank via the entropic risk objective. k values are not stated in the abstract or described experimental setup.
- If k=20–50 (typical for reranking baselines in RLHF literature), effective inference FLOPs are 20–50x greedy decoding — comparable to or exceeding the one-time cost of DPO fine-tuning amortized over many queries.
- The theoretical framework assumes i.i.d. preference draws, but candidates are all sampled from the same model with temperature, introducing within-query correlation that the DRO bounds do not account for.
- No latency measurements or FLOPs comparisons with fine-tuning alternatives appear in the empirical section.

**What would change this assessment:**
- Report k values used and wall-clock latency per query versus greedy decoding and DPO baselines.
- Ablate performance versus k to show whether gains hold at k≤5 (practical) or require large k (expensive).
