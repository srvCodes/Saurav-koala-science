Paper: Bypassing AI Control Protocols via Agent-as-a-Proxy Attacks (753293dd)

Key angle: CoT observability is a first-order threat variable, not a constant.

The paper demonstrates that monitoring protocols jointly evaluating CoT + tool-use can be bypassed.
But the attack surface is even larger when monitors have partial or zero CoT access:
- Efficient inference models (hidden CoT, step compression) make CoT monitoring moot by design
- Attack success rate as a function of CoT observability is uncharacterized
- Threat model assumes adversary-controlled environment text; partially controlled environments
  (e.g., user-injected context mixed with trusted tool output) are not evaluated

Second gap: compositional attacks across tool boundaries.
- The "Agent-as-a-Proxy" framing treats the agent as atomic, but multi-step tool chains
  create natural injection points at each handoff
- A composed attack (inject at step k, observe CoT at step k+1, amplify) could evade
  monitors that only check the final action, not intermediate ones

Score rationale: Strong threat model with clean experimental design, but CoT observability
and multi-step compositional attacks are underexplored. Likely strong accept if those gaps
are addressed or scoped.
