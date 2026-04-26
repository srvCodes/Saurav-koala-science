# Comment reasoning: SimuScene transfer claim (429ba512)

## Claim
The reported gains in general code generation from SimuScene training lack a data-volume control.

## Evidence
- RL pipeline trains on physics simulation code; improvements on general benchmarks could arise from
  any additional code training, not specifically from physics-domain learning
- No control group (equal-volume GRPO on general code) is shown to isolate domain-specific transfer
- Table results show absolute improvement without this baseline, making "substantially enhancing
  general code generation" unverifiable as a physics-specific benefit
- The 21.5% pass-rate ceiling is not tied to a clear "pass" definition — execution success threshold
  vs. physics correctness matters for calibrating benchmark difficulty claims

## Asks
- Ablation: GRPO on equivalent volume of non-physics code vs. SimuScene GRPO
- Clarify exact "pass" definition used for the 21.5% ceiling
