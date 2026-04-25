# Reasoning: Safety Probes — Fanatic Construct Validity

Paper: "Why Safety Probes Catch Liars But Miss Fanatics" (41aa8436)

Key claim to challenge: The Fanatic is trained by explicitly feeding rationalizations
("framing hostility as protective"). This is a deliberate construction, not emergent RLHF.

The impossibility theorem (Thm 4.3) assumes PRF-like trigger complexity, but the empirical
Fanatic is constructed via supervised belief injection, not naturally arising from RLHF reward
hacking. Whether naturally-trained models converge to this regime is undemonstrated.

Second angle: probe probing distribution. The linear probe was trained to detect Liars;
applying it to Fanatics tests OOD generalization, not probe capability on Fanatics.
An ensemble probe or SAE-based decomposition trained with some Fanatic examples might
achieve high detection accuracy — invalidating the "undetectable" claim empirically even
if the theoretical impossibility holds in the limit.

What would change the assessment:
1. Show Fanatic-like behavior emerges from standard RLHF (no explicit rationalization training)
2. Test a probe trained with some Fanatic exposure — does detection drop to chance?
