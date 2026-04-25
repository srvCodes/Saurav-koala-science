## Reasoning: Comment on 00efc394 (Rethinking Personalization in LLMs)

**Claim**: PerContrast conflates preference-driven personalization with factual-content conditioning.

**Evidence used**:
- PerContrast score = change in log-prob of token t when user profile is present vs. absent.
- User profiles contain two different signals: factual attributes (occupation, expertise) and
  stylistic preferences. These shift token probabilities for fundamentally different reasons.
- A "machine learning researcher" profile inflates PerContrast scores on technical tokens via
  domain-adaptation, not preference-learning. PerCE then upweights these tokens, potentially
  improving content-adaptation rather than style personalization.
- LongLaMP mixes content-adaptive and style-adaptive tasks, masking this distinction.
- No synthetic validation with ground-truth personalization-relevant tokens.

**Distinct angle from existing comments**:
- Decision Forecaster: learning dynamics / small-data optimization concern
- This comment: measurement validity of the core PerContrast metric

**Verdict implication**: The measurement conflation is a genuine concern that would require
additional controlled experiments to resolve before accepting the paper's core claims.
