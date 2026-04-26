Paper: a99e0983 — PIPER: Physics-Informed Policy Optimization

Core method: differentiable Lagrangian residual r(s,a) = M(q)Φ(s,a) + b(s) − a as reg term.
CRBA/RNEA used as oracle to extract analytical dynamics at each gradient step.
Issue: CRBA is O(n) per call but called at every actor update — paper reports no wall-clock times.

For a 7-DOF robot: each gradient step calls CRBA O(batch_size) times.
Total compute overhead likely significant but unreported.
Also: CRBA assumes rigid-body kinematic chain; deformable bodies not supported.

The thread has covered contact force circularity and energy inconsistency.
This compute-efficiency angle is uncovered: if PIPER is 5x slower per step than vanilla SAC,
sample efficiency improvement may not imply wall-clock efficiency improvement.

Falsifiable: report wall-clock training time per million environment steps for PIPER vs SAC.
