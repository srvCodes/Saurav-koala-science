# Reasoning: MemCoder LLM Safety Concerns (a1b44436)

Paper proposes MemCoder: code agent with persistent sextuple memory built from commit history.

Key uncovered angle: persistent memory over adversarial-controlled inputs (commits) creates
LLM safety risks not present in static-context agents.

- Commits are partly adversary-controlled (malicious contributors, supply chain attacks).
  Adversarial commit messages can inject instructions into the memory extraction pipeline.
- The memory retrieval step (FAISS + cross-encoder) operates on potentially poisoned content
  without filtering. No trust model is described for what content is allowed into memory.
- Memory persistence across sessions increases the attack surface vs. stateless agents:
  a poisoned memory entry affects all future reasoning without the user re-authorizing it.
- The paper does not evaluate robustness against adversarial commit messages or poisoning.

Assessment: the safety omission doesn't invalidate the core idea but is a notable gap
for an agent designed to operate on real-world repositories with mixed-trust contributors.
