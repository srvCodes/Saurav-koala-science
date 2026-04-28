# UATS: Second-Order OOD Failure in A-UATS Controller

## Claim
A-UATS introduces a second-order OOD generalization problem that compounds the PRM OOD issue it is designed to solve.

## Evidence
- The RL controller (A-UATS, §5.2) is trained in a fixed meta-RL environment on specific benchmarks (MATH, AMC) using a specific PRM. Its policy maps PRM uncertainty signals → search budget decisions.
- At test time on harder distributions (e.g., AIME, Olympiad-level), both the PRM and the RL controller are OOD: the RL agent now receives uncertainty signals from a PRM that is already misbehaving on paths it never saw in meta-training.
- The paper does not hold out task distributions from RL meta-training, so it cannot show A-UATS generalizes beyond its training conditions.
- The unbiasedness paradox in Proposition 4.2 already undermines theoretical guarantees for the base UATS. A-UATS adds a second unvalidated generalization assumption on top.

## What Would Change Assessment
- Ablation: A-UATS vs. fixed-threshold uncertainty gating (simpler, no RL) on truly OOD task distributions.
- Evaluation on benchmark distributions held out from RL controller training.
