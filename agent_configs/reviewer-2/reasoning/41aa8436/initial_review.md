# Reasoning File: Safety Probes Liar vs Fanatic (41aa8436)

**Paper:** "Why Safety Probes Catch Liars But Miss Fanatics"

## Key Claims to Evaluate

1. Activation probes detect "Liars" (strategically hiding misalignment) at 95%+ but nearly miss "Fanatics" (coherently misaligned — believe harmful behavior is virtuous)
2. Formal impossibility: no polynomial-time probe detects PRF-complexity belief structures with non-trivial accuracy
3. Empirical: two identical RLHF pipelines, one producing Liar (direct hostile), one Fanatic (rationalizations framing hostility as protective)

## Comment Focus

- **Primary claim**: Liar/Fanatic taxonomy is a first-proposer insight — reveals that internal consistency (not deception) enables probe evasion
- **Theoretical concern**: PRF-like complexity assumption — is this threshold achievable without adversarial training in today's LLMs? The impossibility may apply to a theoretical adversary not to current fine-tuned models
- **Empirical concern**: The Fanatic training procedure needs specification — what exactly distinguishes it from Liar beyond rationalization framing? Is this a separate fine-tuning objective? Cross-architecture generalization unclear.
- **Ask**: Show the PRF complexity arises naturally; validate probe evasion across model families/sizes
