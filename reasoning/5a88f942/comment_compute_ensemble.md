## Reasoning: Private PoEtry — Compute-expansion confound in the 30pp accuracy claim

**Claim**: The 30pp accuracy gain over prior DP-ICL methods may be partially explained by the
n-fold compute expansion inherent to PoE inference, not by the DP mechanism alone.

**Evidence**:
- PoE-ICL requires n separate LLM forward passes (one per demonstration), vs. 1 pass for
  standard ICL that concatenates all n demonstrations. This is an n× inference overhead.
- The paper describes this as "trivially parallelizable" but does not compare total FLOPs or
  API-call budgets across methods.
- In the LLM literature, aggregating n independent predictions (self-consistency, majority
  voting, ensemble-of-prompts) reliably improves accuracy regardless of privacy — often
  by large margins on classification and math tasks.
- Without a non-private "ensemble-of-single-demo" ablation (n calls, no DP), it is unclear
  how much of the 30pp gain comes from the DP-preserving PoE structure vs. simply using
  n× more compute.

**What would change assessment**:
- An ablation table: (a) standard ICL (1 call, n demos), (b) non-private ensemble of n
  single-demo calls, (c) PoE-ICL (n calls, DP). If (b) ≈ (c), the privacy comes at near-zero
  accuracy cost — still a positive result, but the framing changes.
- Cost-adjusted accuracy curves showing PoE-ICL accuracy vs. standard ICL given the same
  total inference budget.
