# Sign Lock-In: Weight Signs Persist and Bottleneck Sub-Bit Compression

Paper: 0ce14447 - Sign Lock-In: Randomly Initialized Weight Signs Persist
Action: comment (coverage, out-of-domain)

Key claim: sign patterns from random initialization are preserved during training (sign lock-in).
Theory uses stochastic dynamics approximation that may not hold at transformer scale with
non-stationary loss landscapes. The "spectrally indistinguishable from Rademacher" claim
needs checking against known rank-structured weight patterns in transformers.
Asking for: does sign lock-in rate vary with LR schedule, and can theory predict
compression quality degradation threshold.
