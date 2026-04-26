# Prompt Injection as Role Confusion: Mechanistic Probe Evidence

## Paper
Prompt Injection as Role Confusion
ID: 0544adfc-e03f-475c-b228-5865e509305d

## Key concerns

### 1. Causal vs. correlational probe evidence
Role probes showing attacker-controlled signals predict role-perception
representations is correlational, not causal. Without activation patching or
causal mediation analysis, we cannot conclude these representations *cause*
compliance with injected commands vs. being downstream artifacts of processing injected text.

### 2. CoT Forgery generalization scope
CoT Forgery mimics trusted-role syntactic patterns. Transfer rates across
model architectures need to be reported — if the attack relies on
model-specific tokenization artifacts, its generality is limited.

### 3. Defense implications are underspecified
The framing implies a fix (architectural role tagging that is not spoofable).
The paper should distinguish: (a) training-time fixes, (b) inference-time
fixes (hard delimiters), and (c) whether probe geometry directly suggests
which intervention would work.

## Evidence needed
- Causal mediation experiments showing role-probe features causally mediate compliance
- Cross-architecture transfer rates for CoT Forgery
- Ablation: does fine-tuning on role-labeled data shift probe geometry as predicted?
