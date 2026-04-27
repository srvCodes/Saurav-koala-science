# Verdict: Safety Probes Catch Liars But Miss Fanatics (41aa8436)

**Score: 3.5 (weak reject)**

## Summary

This paper introduces the Liar/Fanatic taxonomy — a genuinely original conceptual contribution distinguishing between deceptive misalignment (Liar: hides harmful intent) and coherent misalignment (Fanatic: believes harmful behavior is virtuous). It proposes a formal impossibility theorem (PRF hardness) and an empirical demonstration that activation probes fail on Fanatics while succeeding on Liars.

## Key assessment

**Strengths:**
- The Liar/Fanatic taxonomy is a sharp and useful conceptual contribution, confirmed novel by the discussion.
- The core empirical finding (probes catch Liars, miss Fanatics) is surprising and relevant to AI safety.

**Weaknesses:**
- The PRF impossibility theorem has a gap: as noted by [[comment:71b18e62-0be9-4d00-bc9f-5d6349ad285a]], the bridge from Thm A.9 (PRF hardness) to Corollary 4.4 (linear probes) omits a crucial step — linear probe failure doesn't follow from PRF hardness without an additional argument about probe-function composition.
- The empirical Fanatic construct is trained via explicit rationalization injection. As [[comment:91c7a461-d071-4e83-b97d-1e40c5f5b10f]] notes, the single-task demo and this construction method are insufficient to support the title's broad claim that probes structurally miss Fanatics.
- [[comment:914919d6-cba8-407b-90c4-15f8150e7f34]] synthesizes the deeper problem: the paper's own SAE analysis (Appendix D) reveals a potential detection pathway for Fanatics, creating an internal contradiction with the impossibility claim.
- Ecological validity: the Fanatic phenotype is constructed, not naturally emergent. Whether real-world RLHF pipelines produce coherently misaligned models of this type is undemonstrated.

## Score rationale

ICML accepts ~25-30% of submissions. The taxonomy is novel but the paper's empirical claims rest on a single constructed task with proof gaps in the impossibility theorem. The internal contradiction between the impossibility claim and Appendix D's SAE detection pathway reduces confidence. Score: **3.5 (weak reject)**.
