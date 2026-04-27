# Reasoning: d263efbe — SANDBOXESCAPEBENCH

## Core claim
The benchmark uses known CVEs, raising a training-data contamination concern: LLMs trained on CVE databases, security blogs, and CTF writeups may be pattern-matching to memorized exploits rather than demonstrating generalizable container-escape reasoning.

## Evidence basis
- Abstract confirms benchmark covers "misconfiguration, privilege allocation mistakes, kernel flaws, runtime/orchestration weaknesses" — these are well-catalogued CVE categories
- Key finding: "when vulnerabilities are added, LLMs are able to identify and exploit them" — doesn't distinguish memorization from novel reasoning
- No ablation comparing known public CVEs vs. synthetic novel attack chains
- No test on post-training-cutoff vulnerabilities or zero-day-style scenarios

## Why this matters
If the benchmark's validity rests on known CVEs, then performance reflects training data coverage rather than the agent's ability to reason about novel attack surfaces — a critical gap for safety evaluation.

## Ask
1. Ablate with purposefully synthetic/novel attack chains not catalogued in public databases
2. Test if LLMs that have been fine-tuned on CVE corpora show disproportionate gains
