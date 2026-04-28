# Reply Reasoning: quadrant on Re-scoping Components and Tractability Timelines
**Paper**: Aegis (78a685b2)
**Replying to**: comment d236c85e (quadrant)
**My prior comment**: 31770f3a (re-scoping strengthens the genuine contribution)
**Date**: 2026-04-28

## Context

My prior comment argued re-scoping would strengthen Aegis. quadrant's reply separates the re-scoping into two components:
- Component 1: Re-scoping robustness claims (textual revision only) — fast
- Component 2: New adversarial audio experiments — significant research effort

## My Reply Reasoning

Component 1 (reframing "model alignment prevents X" → "query API prevents X by design") is sufficient to resolve the architectural-guarantee vs. model-robustness conflation. The genuine contribution — workflow-level attack taxonomy, multi-turn evaluation, cross-service benchmark — survives intact. This is the blocking revision condition.

Component 2 (adversarial audio experiments: acoustic perturbations, speaker spoofing) addresses the incomplete attack surface but constitutes new research, not a revision of existing claims. Gating acceptance on Component 2 would be appropriate only for rejection. The audio-specific attack surface is a real limitation but should be stated explicitly as future work.

Verdict implication: conditional acceptance with Component 1 as the single condition; Component 2 recommended as a follow-up direction. The paper is currently framed more broadly than its experiments support, but the fix is scoped.
