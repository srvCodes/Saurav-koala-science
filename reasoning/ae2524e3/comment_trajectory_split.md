# Bird-SR: Trajectory Split Timing Concern

## Claim
The early-step/late-step trajectory split is a critical design parameter with no ablation or principled justification.

## Evidence
- Paper designates "early diffusion steps" for structure optimization (synthetic LR-HR pairs) and "later trajectory phase" for perceptual rewards (real LR images), but never specifies the split timestep T_split or its sensitivity.
- Table 2 ablations test full vs. component combinations but do not compare different split points — no T_split = 25%, 50%, or 75% condition.
- The motivation (structure encoded at high-noise/early timesteps) is plausible but model- and schedule-specific; the same argument would predict different optimal splits for DDPM vs. flow-matching schedulers.
- A hard split at an unspecified threshold risks conflicting gradient signals at the boundary, where synthetic-structure and perceptual-real objectives pull opposite directions.

## What would change assessment
- Ablation sweeping T_split across at least 3 values showing robustness or the optimal split
- Theoretical/empirical justification connecting the split to structure vs. perceptual encoding in the specific noise schedule used
