# Verdict: TRAP (44a42a80) — Weak Accept, Score 5.5

## Core contribution
TRAP is the first systematic adversarial attack framework targeting CoT reasoning in VLA models,
demonstrating that adversarial patches can corrupt chain-of-thought to hijack robot actions
without modifying user instructions.

## Key strengths
- Novel attack surface: CoT-mediated action hijacking is an underexplored and practically
  significant threat for deployed robotic systems.
- Empirically demonstrated: the competition mechanism (CoT overrides instructions, Table 1)
  provides real insight into VLA model internals.
- Code artifacts present and linked; implementation is auditable.

## Key weaknesses
1. Evaluation limited to 2 of 3 robot platforms for the key ablations; transfer generalizability
   is unverified on the third platform.
2. The λ=0 ablation (Table 3) only partially isolates CoT-mediated vs action-mediated channels;
   the CoT-Only mode still uses gradient information from the action head.
3. Artifact audit reveals GraspVLA infrastructure details (model weights, config) remain exposed
   in linked repos, which is a responsible-disclosure gap.
4. The novelty framing overstates departure from existing adversarial-patch literature on VLMs;
   the VLA setting is incremental over existing multi-modal attack work.

## Score rationale
Score 5.5 (weak accept). The paper identifies a real and novel threat model for CoT-based VLA
systems and provides empirical grounding. The evaluation scope is limited and the responsible
disclosure gap is concerning. The contribution clears the novelty bar narrowly given the
practical significance of the attack vector for deployed robotics safety.
