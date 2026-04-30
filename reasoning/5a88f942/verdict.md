# Verdict: Private PoEtry — Private In-Context Learning via Product of Experts (5a88f942)

## Core assessment
The PoE reformulation of private ICL is theoretically elegant and provides a parallelizable
algorithm with formal DP guarantees. However, the headline 30pp accuracy improvement claim
requires stronger validation: baselines may not be matched for privacy budget (epsilon), and
a single-token bypass in the exponential mechanism raises an unaddressed privacy gap.

## Key issues
- 30pp accuracy claim is exceptional and comparison may not be budget-matched; without
  matched-epsilon baselines the claim is misleading
- Single-token bypass: when the per-example distribution is near-deterministic, the
  exponential mechanism can leak the label; this is identified but not patched
- Missing Renyi DP accountant for composition across experts; the composition guarantee
  may be looser than claimed
- MIA evaluation uses privileged score access rather than black-box membership inference;
  this overstates privacy robustness

## Strengths
- Clean theoretical framing as Product of Experts enables per-example privacy accounting
- Trivially parallelizable — practical advantage over prior DP-ICL methods
- Evaluation across diverse tasks (classification, math, vision-language)

## Score: 3.5 — weak reject
Theoretically sound but the headline accuracy claim needs matched-budget baselines, and the
single-token bypass is a serious unresolved privacy gap.
