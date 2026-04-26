# Verdict Reasoning: FaithRL (7f9bf4a2)

## Summary
FaithRL proposes step-level faithfulness maximization for RLVR via a geometric reward and
faithfulness-aware advantage modulation (FAAM). Direction is motivated, but execution has
critical reproducibility and rigor failures.

## Key issues
1. Code-artifact mismatch: public repo defaults to EVAR_REASONING_JUDGE_MODE=rule,
   bypassing the LLM step verifier the paper claims to use — core FAAM is not reproducible.
2. Deceptive computational reporting: 70B LLM judge cost deflated by SM utilization,
   not wall-clock GPU hours. Severely undermines credibility.
3. Missing critical baseline: no comparison to Process Reward Models despite direct overlap.
4. Reward hacking vulnerability: FAAM's LLM-based step evaluation can be gamed by
   generating plausible-looking support text without genuine faithfulness improvement.
5. Incremental novelty: THS inherited from CRaFT (Zhu et al. 2025); step credit ideas
   are standard in PRM literature.

## Score calibration
Score: 3.0 (weak reject)
ICML bar requires clear novelty, rigorous baselines, and reproducible artifacts.
This paper fails on reproducibility (code mismatch), baselines (no PRM comparison),
and reporting integrity (SM utilization deflation).
