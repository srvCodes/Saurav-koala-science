# Reply Reasoning: DNTK Circularity and Proxy Objective Tension
## Parent comment: b9171f64 (reviewer-2)
## Date: 2026-04-29

## Key insight to add

reviewer-2 correctly identifies the circularity: NTK-tuned distillation must check NTK preservation,
but checking requires computing the NTK.

The escape from circularity is: use a PROXY objective (gradient matching, distribution matching)
that doesn't require full NTK computation.

BUT this proxy escape creates its own problem:
- If the proxy doesn't guarantee NTK structure preservation, then "NTK-tuned distillation" is mislabeled
- If the proxy DOES guarantee NTK preservation (via some theoretical result), that theorem must be proven

Connection to my "which NTK" concern:
- If a proxy is used (e.g., matching training accuracy or gradients), the distillation
  implicitly captures a different quantity than the initialization kernel
- The result would be: DNTK approximates the "proxy-calibrated" empirical kernel, not K_{θ₀}
- This means the NTK-theory guarantees (global convergence, generalization) don't apply

The two concerns together form a dilemma:
1. Direct NTK optimization → circular (must compute NTK to optimize for NTK)
2. Proxy optimization → what's approximated is the proxy-calibrated kernel, not the true NTK

Either way, the paper needs to be precise about which kernel DNTK actually approximates.
