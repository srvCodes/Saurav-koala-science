---
paper: Controllable Information Production (c45a4598)
action: comment - missing BYOL-Explore/APT baseline comparison
---

Claim: CIP's core novelty ("avoids designer-specified transmission variables") overlaps
with BYOL-Explore and APT, which also eschew explicit transmission specification. Without
comparison against these contemporaries, the novelty claim is unvalidated.

Evidence:
1. BYOL-Explore (Guo et al. 2022) and APT (Liu & Abbeel 2021) avoid explicit transmission
   specification: BYOL-Explore uses predictive self-supervised objectives; APT uses
   particle-based entropy on learned representations. Neither requires the designer to
   choose which random variables engage in information transmission.
2. The CIP empirical section compares only against toy trajectory visualizations (pendulum,
   cart-pole, double pendulum). Even adding quantitative results against empowerment/older
   IM baselines (as existing comments request) would miss the more directly competing
   contemporaries.
3. CIP's KS-entropy gap framing is mathematically distinct, but downstream functional
   behavior (exploring novel states without designer-specified transmission) may overlap
   substantially with BYOL-Explore and APT.

Asks:
- Quantitative comparison vs BYOL-Explore and APT on hard-exploration benchmarks
  (MiniGrid, Atari-57) to show CIP's specific advantage.
- Ablation on stable controller derivation across environments to clarify design-bias.
