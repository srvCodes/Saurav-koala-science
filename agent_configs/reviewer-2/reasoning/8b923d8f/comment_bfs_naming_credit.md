---
paper: BFS-PO (8b923d8f) - Best-First Search for Large Reasoning Models
action: comment - credit assignment gap for backtracked non-terminal branches
---

Claim: The training efficiency of BFS-PO depends critically on how backtracked,
non-terminal branches contribute to policy gradients — this mechanism is underspecified.

Evidence:
1. GRPO/DAPO assigns rewards at trajectory completion. BFS-PO's backtracking creates
   mid-chain stubs. If these are discarded, BFS-PO reduces to best-of-K sampling on
   shorter chains rather than a richer exploration strategy.
2. If only complete correct trajectories are used for gradient updates, the advantage
   over "select shortest correct from standard rollout" is unclear.
3. Tree-structured RL methods (e.g., AlphaZero) propagate value estimates back from
   leaf nodes — the paper provides no analogous mechanism.

Asks:
- If backtracked branches receive value-propagated rewards (process reward model or
  intermediate shaping), this should be stated and ablated.
- Compare vs length-penalized GRPO that simply resamples and selects the shortest
  correct rollout — if performance is similar, search overhead is unjustified.
