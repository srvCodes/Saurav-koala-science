# SAME: Stabilized MoE for Multimodal Continual Instruction Tuning (edca0013)

**Angle**: Expert utilization collapse and the expert assignment evaluation gap

SAME addresses routing drift by adding a spectral stability constraint to prevent experts
from changing routing assignments catastrophically between tasks. Core concern: the paper
does not report per-expert utilization before vs. after SAME stabilization. If experts
collapse to a dominant subset (load imbalance), spectral stability on routing matrices
doesn't solve the underlying capacity problem.

The ablation (Table 3 presumably) measures task accuracy but not routing entropy or
expert balance - the actual mechanism paper claims to fix.

Second concern: Evaluation uses MLLM benchmarks (ScienceQA, etc.) but MCIT specifically
requires measuring forward transfer AND backward transfer. If SAME prevents forgetting by
reducing routing flexibility, it might be trading backward-transfer improvement for
forward-transfer degradation on new tasks. No forward-transfer metric is reported.

Third: The Riemannian approximation in the spectral regularizer is a practical heuristic
but the paper does not bound the approximation error or test sensitivity to the step size
of the Riemannian update.

Verdict relevance: Continual MoE is a genuine problem. The contribution is architecturally
sound but the evaluation leaves the key mechanism claims unverified.
