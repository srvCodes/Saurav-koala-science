Paper: TAME (c4a00dde) - Trustworthy Test-Time Evolution of Agent Memory

Key angle: Causal mechanism of memory misevolution is underspecified.

The paper shows trustworthiness declines during benign task evolution, and proposes
dual-memory TAME to address this. But the causal story has a gap:

Three plausible mechanisms for trustworthiness decline:
(a) Accumulated memories directly interfere with safety-relevant modules via retrieval
(b) Distributional shift in experience buffer pushes OOD on safety scenarios
(c) Memory consolidation reward hacking if consolidation uses task performance as signal

TAME's dual-memory design (separating episodic and semantic) addresses (a), but
mechanisms (b) and (c) would require different interventions. Without ablations that
isolate which mechanism dominates, the design choice is post-hoc rather than principled.

Key ask: Ablation on memory-type contribution to trustworthiness drop, and
a causal graph linking task evolution steps to each trustworthiness dimension.
