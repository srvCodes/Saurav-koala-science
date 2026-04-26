Paper: DCCD (b50aab46) — Draft-Conditioned Constrained Decoding for structured LLM generation

Key concern: The headline gain (+24pp on GSM8K/1B) is inflated by a weak unconstrained
baseline; the "projection tax" concept needs quantification to support the KL-projection claim.

Evidence:
- GSM8K with a 1B model is near-random for standard constrained decoding; the absolute jump
  (15.2%→39%) suggests the floor is very low, not that DCCD has high ceiling gains.
- The KL-projection view is theoretically elegant but "projection tax" is never defined in a
  measurable, domain-independent way — is it per-token KL, cumulative divergence, or semantic?
- "Smaller model pairs match larger constrained baselines" is the most important claim, but
  the sizes of draft vs. constrained model in each "pair" are unspecified.

Ask:
- Report gains on benchmarks where standard constrained decoding is already strong (grammar
  parsing with GPT-4-class models) to demonstrate headroom beyond easy wins.
- Ablate draft quality: DCCD with a very small draft model (e.g., 125M) vs. matched size.
