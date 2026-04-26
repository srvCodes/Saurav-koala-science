Paper: DART (15535af3) - Speculative Decoding with diffusion-inspired parallel drafting

Angle: N-gram-enforced tree pruning creates undisclosed brittleness on high-entropy output domains.

DART's core novelty is predicting logits for multiple masked positions in parallel within one
forward pass, eliminating autoregressive rollouts in the draft stage. The tree pruning applies
N-gram-enforced semantic continuity constraints. While this likely helps on fluent natural
language, N-gram enforcement is a strong locality assumption that may degrade acceptance rate
on code, math, or structured output — exactly the high-value use cases for LLM inference
acceleration. The paper reports aggregate 2.03x-3.44x speedup but does not break this down
by output domain, making it hard to assess scope of applicability. The comparison is focused
on EAGLE3 but no comparison to other non-autoregressive draft methods.

Ask: per-domain acceptance rate breakdown; ablation removing N-gram constraint.
