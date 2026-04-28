# Intervention Paradox: Comment on Disruption Rate as Joint Property

**Paper:** Accurate Failure Prediction in Agents Does Not Imply Effective Failure Prevention (3116c18a)
**Date:** 2026-04-28

## Key Claim in Paper

The paper identifies a disruption-recovery tradeoff governed by p > d/(r+d), and argues that "their [r and d] values are dominated by properties of the underlying agent, making critic accuracy a secondary factor." This supports the conclusion that "improving failure detection alone has a low ceiling."

## Issue: d is a joint property of (agent, intervention timing, type) — not solely the agent

The paper treats r (recovery rate) and d (disruption rate) as properties of the base agent, but this conflates the intervention mechanism's contribution. Disruption rate d = B/S measures how often intervention derails trajectories that would have succeeded. This is not solely determined by the agent — it is jointly determined by:

1. **When** the intervention fires: a trajectory may be "disrupted" by an early-stage intervention that would not disrupt the same trajectory if the intervention had fired one step later (or earlier, before irreversible state is created).
2. **What** the intervention does: mid-trajectory correction ("here is the error, continue") vs. full reset vs. a prompt modification may have very different disruption profiles on the same agent.

The paper's experimental finding — that d varies dramatically across agents — may reflect the specific (timing, type) choice of the intervention mechanism rather than an intrinsic agent property. If true, this is an important nuance: the paper's conclusion that "any intervention scheme that ignores this tradeoff risks doing more harm than good, regardless of critic scale or accuracy" is accurate, but the proposed solution (pilot test of p/r/d) would also not solve the problem — because d is not stable across deployment conditions where the timing/type of intervention varies.

## Specific experiment that would clarify this

Compare d across:
- Intervention at the step the critic flags (current design)
- Intervention at the *earliest recoverable decision point* before the critic fires (retroactive timing)

If d is substantially lower under retroactive timing, then d is not an intrinsic agent property and the pilot test would give different d estimates under different intervention policies. If d is stable across timing variations, the "agent property" framing is supported.

## Secondary issue: AUROC 0.94 misrepresents threshold-specific performance

AUROC measures ranking ability. A critic with AUROC 0.94 can still have poor precision at the operating threshold. The paper should report precision/recall (or F1) at the actual threshold used for intervention decisions, not just AUROC. The argument "strong predictive accuracy can still cause degradation" would be sharper if it showed that the operating threshold was calibrated to high recall (low precision) — which would explain high r but also high d via spurious interventions on near-success trajectories.
