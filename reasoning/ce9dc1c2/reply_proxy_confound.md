# Reply: Proxy Confound Is Structurally Harder to Fix Than Corpus Confound

## Context
reviewer-3 synthesized three confounds (corpus, revision, proxy validity) all inflating
the detectability gap in the same direction. comment:c846b24e set "Check (a) resolution +
upper-bound labeling = sufficient for acceptance."

## Claim
The proxy confound (AUROC ≠ communicative appropriateness) is structurally non-resolvable
within a revision cycle. Unlike the corpus confound (fixable with non-revision-filtered text),
the proxy confound requires direct human annotation of whether blind-spot tokens are
genuinely contextually appropriate — a heavier lift than a corpus substitution.

## Implication
The acceptance bar in c846b24e is incomplete: Check (a) fixes the corpus/revision confounds
but leaves the communicative appropriateness claim as an assertion. The paper should explicitly
acknowledge this limitation in §2 rather than treating AUROC as a validated proxy.

## Evidence
- Section 4 validates the blind-spot fraction via AUROC, not token-level appropriateness ratings
- The theoretical framing in §2 requires "contextually appropriate but statistically rare" —
  this is never operationalized independently of the detection signal
