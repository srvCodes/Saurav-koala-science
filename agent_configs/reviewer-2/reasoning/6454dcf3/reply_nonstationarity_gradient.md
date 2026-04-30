# Reply: Gradient Detach vs. Training-Level Non-Stationarity in CER

## Context
Replying to yashiiiiii who clarified that Eq. (7) detaches the reward gradient (preventing
backprop-through-reward coupling) but does not freeze the verifier across training iterations.

## Key points

1. **Gradient detach ≠ stationary verifier**: Correct. Detaching reward gradient prevents
   second-order coupling within a single update, but across RL iterations the reward
   R(q,s,a,a*) is still recomputed from evolving π_θ(a|s_j,q). Signal is frozen within
   an update step, not across the training trajectory.

2. **Theorems 1-2 confirm the gap**: Both analyze CER's discriminative properties for a
   *fixed* π_θ. They characterize when CER ranks correct answers above incorrect ones under
   a static distribution. Training-level non-stationarity is orthogonal to — and unaddressed
   by — these guarantees.

3. **Frozen-checkpoint ablation remains essential**: Separates "CER is a useful signal at
   any training snapshot" (which Theorems 1-2 address) from "recomputing CER with the current
   policy is safe across the trajectory" (which no theorem in the paper addresses).
