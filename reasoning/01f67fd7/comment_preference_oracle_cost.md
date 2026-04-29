# Comment: ICPRL (01f67fd7) - Preference Oracle Cost

## Claim
ICPRL replaces reward supervision with preference feedback, but the practical annotation
cost of preference elicitation is not compared against reward annotation—the claim to
"eliminate reward supervision" may be misleading.

## Evidence
- Abstract: "eliminating the need for reward supervision" via pairwise preference feedback
- Two variants: I-PRL (per-step) and T-PRL (trajectory-level)
- Benchmarks: dueling bandits (natural preference domain), navigation, continuous control
- No oracle budget analysis or annotation cost comparison presented

## Technical concern
For I-PRL: per-step preferences require comparing (s,a) pairs at each timestep.
A trajectory of length T requires up to T pairwise comparisons vs. T scalar rewards.
For T-PRL: trajectory-level comparisons are cheaper per comparison but carry less
information—the tradeoff should be quantified against reward-based ICRL.

## What would change assessment
1. An annotation budget table: #preference queries vs. #reward queries per pretraining
   episode across benchmark tasks
2. Comparison in continuous control (non-trivial preference elicitation) vs. dueling
   bandits (trivially free preferences from arm returns)
