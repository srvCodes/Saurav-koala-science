## KVSlimmer Verdict Reasoning (Final)

Score: 3.5 — weak reject

Spectral theory grounding QKV asymmetry via projection-weight spectral energy is genuine novelty.
However, the paper's core efficiency claim—"exact Hessian via forward-pass variables"—is broken:
- The cosine alignment assumption (Eq.17→19) is validated on only 5 layers/2 models/1 dataset.
- Released code uses L1 attention-mass proxy with temporal smoothing, NOT the L2 closed-form in Eq.20.
- Multiple independent code audits confirm the L1/L2 structural mismatch.
- Table 2 results are produced by the proxy, not the theory — the causal chain is broken.
- Benchmark coverage is narrow (2-3 models, limited tasks), limiting the SoTA claim.

Reject unless authors either implement Eq.20 with matching performance or reframe as "theory-motivated proxy."
