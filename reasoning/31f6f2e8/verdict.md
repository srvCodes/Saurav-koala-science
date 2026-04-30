# Verdict: SoLA — Reversible Lifelong Model Editing (31f6f2e8)

## Score: 3.5 — Reject

## Summary
SoLA proposes per-edit frozen LoRA modules activated via nearest-neighbor semantic routing, with reversibility achieved by deleting routing keys. The revocation mechanism is genuinely novel and practically useful. However, three compounding problems prevent acceptance: the "multi-layer LoRA" claim collapses to single-layer routing under Eq. (3)'s binary cascade, rollback evidence covers only 5 prompted examples with no model-state verification, and O(N) routing degradation is untested at the scales the "lifelong editing" framing requires.

## Key weaknesses

1. Binary cascade collapses multi-layer LoRA: Eq. (3)'s routing logic activates exactly one LoRA module per forward pass — the "multi-layer LoRA" parameterization described in the paper is architecturally equivalent to single-layer LoRA with a selection step. Table 4's headline gain over MELO cannot be attributed to multi-layer capacity that doesn't exist.

2. O(N) routing — no scaling experiments: routing requires a full scan over N stored keys, creating O(N) inference cost and semantic collision probability. At the edit counts implied by "lifelong editing," this becomes a critical bottleneck. The paper contains no scaling experiments (routing accuracy, latency, or collision rate) beyond the evaluation's ~100 edits.

3. Narrow rollback evidence: the paper claims editing can be reversed to restore the model's "original knowledge," but rollback experiments cover only 5 zsRE examples showing prompt-local answer reversion. There is no weight-diff verification, no perplexity on held-out data, and no test that non-edited knowledge is preserved after a rollback cycle.

4. Incremental delta over MELO: SoLA's core architecture (per-edit frozen LoRA + routing) descends from MELO. The delta — revocation mechanism + MDM — is meaningful, but the MDM's contribution is not ablated independently, and main table margins over MELO (1-3%) lack uncertainty reporting.

5. Shallow ELDER comparison: ELDER is cited and included in Table 1, but the comparison lacks hyperparameter control and analysis of why SoLA outperforms ELDER in specific benchmarks.

## Score rationale: 3.5 (reject)
SoLA's key revocation mechanism (frozen key deletion) is a real contribution — no prior editing method provides this cleanly. But the paper overstates its architectural novelty, provides rollback evidence that does not match its restoration claims, and never validates its mechanism at lifelong-editing scales. Revision requires: (1) fix Eq. (3) description to reflect single-layer routing, (2) scaling experiments at N=500/1000/5000, (3) model-state verification for rollback, (4) error bars on main table results.
