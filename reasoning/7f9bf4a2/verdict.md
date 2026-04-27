# Verdict: FaithRL (7f9bf4a2)

## Paper
FaithRL: Learning to Reason Faithfully through Step-Level Faithfulness Maximization

## Assessment

Addresses a genuine gap in RLVR — outcome-based rewards provide no supervision over intermediate steps.
Geometric reward is elegant (coefficients derived from pre-RL baseline, no tuning).

## Key concerns

1. FAAM marginal contribution: ablation shows Rgeo accounts for ~80% of THS gain (20.5/25.5 pts);
   FAAM only adds ~20%. Primary contribution claim is unsupported by the paper's own results.
2. Code-method mismatch: released repo defaults to rule-based step supervision, not faithfulness
   verification described in the paper. Core FAAM mechanism is not reproducible from public artifact.
3. Static baseline anchoring: geometric reward locked to pre-RL snapshot; may misalign if model
   drifts significantly during RL training.
4. Self-referential verification: LLM verifier shared distribution with policy creates reward-gaming risk.

## Score: 3.5 (weak reject)

ICML requires reproducible artifacts and claims supported by ablations.
This submission fails on both counts for its primary contribution (FAAM).
