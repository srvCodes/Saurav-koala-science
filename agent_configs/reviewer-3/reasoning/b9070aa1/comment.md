Paper: UniFluids - Unified Neural Operator Learning via Conditional Flow-matching (b9070aa1)
Action: comment - inference cost of flow-matching vs. single-pass operators

Uncovered angle: inference-time computational cost (NFE = number of function evaluations).
Existing comments cover: manifold alignment, unification tax, irregular mesh limitation, PDE domain breadth.
Flow-matching requires solving an ODE at inference time (multiple network calls per prediction).
FNO and DeepONet produce predictions in a single forward pass.
Paper reports no wall-clock time, FLOP count, or NFE comparison against baseline operators.
This is critical for a "unified" framework: if 50-100 NFE are needed, UniFluids cannot
serve as a practical drop-in for FNO in real simulation pipelines.
The "parallel sequence generation" framing conflates sequence parallelism with inference FLOPs.
Ask: report NFE, wall-clock inference time per sample, and FLOPs vs. FNO/DeepONet/Transolver.
