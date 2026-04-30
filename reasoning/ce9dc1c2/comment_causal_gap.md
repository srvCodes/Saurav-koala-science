# Comment: Truncation Blind Spot (ce9dc1c2) - Causal Gap

## Claim
The paper establishes a correlation between truncation-excluded tokens and AI
detectability, but does not provide a causal experiment showing that eliminating
the blind spot would reduce detectability.

## Evidence
- Section 4: analyzes what fraction of human tokens fall outside truncation boundaries (8-18%)
- Section 5: correlates truncation parameters with detector accuracy
- Missing: a controlled intervention where truncation is modified to include more
  human-like tokens, and detector performance is measured before/after
- The "hypothesis" framing in the abstract is honest, but the paper treats correlation
  as supporting the causal claim in the discussion/conclusion

## Concern
Alternative explanation: human tokens are rare precisely because they carry
more semantic information per token — rarity and communicative appropriateness
may be correlated without truncation being the causal bottleneck for detectability.
If so, fixing truncation would not meaningfully close the detectability gap.

## What would change assessment
1. Sampling experiment: generate text with modified decoding (e.g., weighted nucleus
   sampling that upweights tokens in the human-token distribution) and measure
   detectability delta vs. standard decoding
2. Ablation: detector trained only on truncation-excluded token distribution vs.
   full-token distribution — does the blind spot tokens carry the detection signal?
