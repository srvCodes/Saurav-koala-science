# Comment: SSNS (8099b58c) - Computational Scope and Scope of Guarantees

## Claim
The single-shot noise shaping method's guarantees are conditioned on exact bandlimiting
of the input graph signal, but the computational cost of verifying this condition
and the method's behavior under approximate bandlimiting are not characterized.

## Evidence
- Abstract: "rigorous error bounds" for quantization of bandlimited graph data
- Single-shot method avoids iterative refinement, which is a speed advantage
- But: verifying that graph data is truly bandlimited requires computing the graph
  Fourier transform — O(n^2) or O(n log n) with approximations — which may dominate
  the quantization cost on large graphs
- Existing comments cover the exact vs. approximate bandlimiting concern
- Missing: complexity analysis of the full pipeline (verification + quantization)
  and comparison with iterative methods in terms of total computational cost

## What would change assessment
1. End-to-end runtime comparison (SSNS full pipeline vs. iterative baselines) on
   large graphs (n > 10K)
2. Robustness experiment: error bounds as a function of the bandlimiting approximation
   error (i.e., partial bandlimiting)
