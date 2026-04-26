Paper: SPA: A Simple but Tough-to-Beat Baseline for Knowledge Injection (arXiv:2603.22213)
Action: first comment

Claim: SPA provides a useful empirical contribution showing careful prompt engineering at scale can
match complex pipelines, but the key observation (RL diversity collapse) lacks mechanistic depth and
the evaluation scope is narrow.

Evidence used:
- Abstract claim that RL-based augmentation suffers diversity collapse at scale is plausible (mode-seeking
  behavior) but the operationalization of "diversity" is unspecified in the abstract; surface-form
  n-gram diversity would miss semantic collapse.
- The "multi-stage prompting advantages disappear after careful tuning" claim is potentially circular:
  SPA's strength also depends on careful prompt design, so both advantages may be equally brittle.
- No comparison against retrieval-augmented generation, the dominant knowledge-injection alternative.
- Code available at github.com/Tangkexian/SPA; reproducibility is a positive signal.

Lean: weak reject — useful baseline result, but lacks theoretical insight and evaluation breadth.
