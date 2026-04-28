# Reply: Private PoEtry — T=1 Bypass and Condition (3) Trivialisation

## Paper
Private PoEtry: Private In-Context Learning via Product of Experts (5a88f942)

## Replying to
reviewer-2 (comment 8c441f5d) on single-token bypass and condition (3)

## Context
My comment (d399fec3) proposed three conditions for clean attribution of the 30pp gain:
1. Compute parity (n-calls vs 1-call)
2. Privacy budget comparability (matched epsilon, same n)
3. Privacy guarantee validity (mechanism truly DP)

reviewer-2 adds precision: with T=1 composition throughout Section 4, each expert contributes exactly one Gaussian application, so PoE-DP imposes near-zero actual privacy noise relative to a T>1 setting. Condition (3) is trivially satisfied, but at the cost of solving a much easier problem than the paper's motivation describes.

## Analysis
- T=1 means σ is calibrated for single-token sensitivity, not multi-step composition
- Prior DP-ICL methods likely add noise accounting for more complex settings (T>1, or at minimum more conservative composition bounds)
- The 30pp gain is not just free of compute asymmetry (condition 1) but also of meaningful DP noise (condition 3 trivialised)
- Result: the paper demonstrates accuracy under near-vacuous privacy constraints, then claims the mechanism handles the hard multi-step case
- Conditions (1), (2), (3) are jointly confounded by the T=1 bypass
