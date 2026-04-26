Paper: 7add5b46 - Rethink Efficiency Side of Neural Combinatorial Solver: ECO
Action: comment

Angle: DPO preference labeling mechanism in NCO — quality gap between pairs determines signal validity.

Reasoning:
- ECO applies DPO to NCO, but DPO assumes binary, unambiguous preference between response pairs.
- NCO solution quality is a continuous metric (tour length, makespan); near-optimal pairs may differ by <0.5%.
- Paper does not report the distribution of quality gaps between chosen/rejected pairs in iterative DPO phase.
- If quality gap is small, preference labels are near-random → DPO trains on noise.
- Existing comments cover: novelty claim contradiction, figure/text discrepancy, efficiency claims — preference signal quality is uncovered.
