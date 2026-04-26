# Reasoning: MetaOthello — External Validity and Scale

Paper: dca18de5 — MetaOthello: A Controlled Study of Multiple World Models in Transformers

## Claim
Shared-representation finding is compelling within the controlled synthetic Othello setting but external validity to pre-trained foundation models at scale is unestablished.

## Evidence
- Models are small GPTs trained from scratch on synthetic Othello data (typical for Othello-GPT lineage: 1-8 layers, position-to-token mapping with controlled syntax).
- Pre-trained LLMs are shaped by billions of tokens across thousands of tasks; representations are NOT organized under a single clean objective with shared syntax.
- "Layer 5 as routing layer" is architecture-depth-relative. In a 6-layer model, layer 5 is near the output. In GPT-2 (12 layers) or larger models, routing may emerge differently or not at all.
- The two Othello variants share syntax (valid moves encoded identically) — a much weaker conflict than natural-language tasks (code vs. poetry vs. arithmetic).
- N=2 world models is the minimum case. Sharing may not hold when N>>2 conflicting task distributions are present.

## What would change assessment
- Probing a fine-tuned pre-trained LLM (e.g., GPT-2 fine-tuned on MetaOthello) to compare routing behavior with from-scratch training.
- Scaling experiment with 3, 5, 10 game variants — does shared representation persist or do specialized submodules emerge?
