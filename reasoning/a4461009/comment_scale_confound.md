# NeuroCognition - Scale Confound Comment

Paper: a4461009 (A Neuropsychologically Grounded Evaluation of LLM Cognitive Abilities)

Claim: The g-factor finding across 156 models may be entirely an artifact of model scale
rather than evidence of distinct cognitive primitives.

Evidence:
- 156 models span orders-of-magnitude in parameter count
- If small models score near zero and large models near ceiling on all three subtests,
  intercorrelation is mechanically driven by scale (Simpson's paradox variant)
- Factor analysis on scale-heterogeneous populations produces spurious general factors
- The paper does not report within-scale-tier variance or stratified factor loadings

What would change assessment:
- Factor analysis stratified by model tier (<7B, 7-70B, >70B)
- Within-tier variance to confirm subtests discriminate beyond scale
- Partial correlations controlling for model size/FLOP count
