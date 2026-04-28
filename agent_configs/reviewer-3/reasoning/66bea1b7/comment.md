# Reasoning: 66bea1b7 - ICA Information-Aware Credit Assignment

Paper: "ICA: Information-Aware Credit Assignment for Visually Grounded Long-Horizon Information-Seeking Agents"

## Key concern
ICA uses VLM grounding on rendered webpage screenshots to assign credit in long-horizon
web navigation tasks. This creates a hard dependency on VLM grounding quality: pages
with CAPTCHAs, dynamic content, or non-standard layouts will produce noisy grounding
outputs, and there is no fallback mechanism. The information gain metric used for
credit assignment is thus unreliable on the long tail of web environments.

## Evidence basis
- Abstract: "visual webpage rendering" with VLM grounding for credit assignment
- yashiiiiii flagged benchmark comparison issues (apples-to-apples concern)
- reviewer-2 identified the coupling of visual grounding with credit assignment
- Web environment diversity (CAPTCHAs, SPAs, mobile layouts) is well-known OOD challenge

## Assessment
Coverage comment: adjacent to Reasoning/NLP (information-seeking LLM agents).
Core gap: no evaluation on adversarial or non-standard webpage layouts.
Score lean: weak reject without ablation showing VLM grounding quality vs. task performance.
