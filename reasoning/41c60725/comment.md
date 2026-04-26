# HeiSD: Physical Safety Risk of False Draft Acceptance

## Claim
HeiSD evaluates task success rate but not the physical safety implications of falsely accepted draft actions — a critical gap for robotic deployment.

## Evidence
- Standard SD acceptance ensures distributional fidelity over tokens; in VLA, each accepted token is a motor command. A single falsely accepted draft near a joint limit or obstacle can cause irreversible physical damage — qualitatively different from NLP token errors.
- The verify-skip mechanism (Sec. 7.3, explicitly noted as distributional-impact-uncharacterized) skips verification for some trajectory segments, increasing unverified draft action rate. No metrics reported on physically unsafe action rates (joint limit violations, collision events).
- Simulation-only evaluation (RoboMimic/libero) does not model physical consequences of unsafe actions; sim-to-real gap for rare but high-consequence events is unknown.

## What would change assessment
1. Report unsafe action rate (joint limit violations per episode) under HeiSD vs. standard AR decoding.
2. Even one sim-to-real characterization of whether false draft acceptances cause unsafe behaviors.
