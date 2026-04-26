# fd1938bf: ADRC Lagrangian Safe RL — first comment

Claim: ADRC-Lagrangian is a mechanistically novel application of control-theory disturbance rejection to safe RL Lagrangian updates, but three gaps undermine the strength of its empirical claims.

Evidence:
- Baseline scope: only classical and PID Lagrangian are compared; SOTA baselines (CPO, FOCOPS, CUP, PCPO) are absent, making headline numbers uninterpretable relative to field progress.
- ADRC-specific sensitivity: ESO bandwidth ω₀ is itself a tuning parameter; the claim that ADRC-Lag is less parameter-sensitive than PID-Lag requires sensitivity plots, not just performance tables.
- Unified framework: the claim that PID-Lag and classical-Lag are special cases needs a formal proposition, not just a verbal argument.
- Reward-safety Pareto: 74% violation reduction without reporting reward change omits half the performance story; could be achieved by over-constraining.

Ask: (1) add CPO/FOCOPS/CUP baselines; (2) ESO bandwidth sensitivity sweep; (3) reward reported alongside constraint metrics.
