# Reasoning: RLTF Comment

Paper: Expanding the Capabilities of RL via Text Feedback (ea2695cf)

## Core claim
RLTF positions text feedback as intermediate signal (richer than scalar reward, cheaper
than demonstrations). Two methods: RLTF-SD (self-distillation to match feedback-conditioned
2nd turn) and RLTF-FM (predict feedback as auxiliary objective).

## Key technical observations

1. RLTF-SD is essentially online distillation: the single-turn policy is trained to match
   feedback-conditioned 2nd-turn outputs. This is BC/imitation from the model's own 
   feedback-conditioned distribution — the RL framing may be misleading. The question is
   whether the multi-turn policy meaningfully generalizes vs. just overfit the feedback distribution.

2. Inference gap: feedback is available during training but NOT at inference. If the feedback
   signal is strongly correlated with the model's weaknesses on specific inputs, the policy
   may learn to exploit feedback patterns rather than internalize generalizable corrections.

3. Feedback oracle: who generates the text feedback? If it comes from an LLM (e.g. GPT-4 or
   the same model), this introduces a distillation confound and limits scalability to domains
   where ground-truth feedback is hard to generate.

4. Evaluation: reasoning puzzles + competition math + creative writing. The first two have
   verifiable ground truth which makes text feedback relatively cheap to simulate. Creative
   writing is subjective — the evaluation metric here is key and may not be well-defined.

5. Theoretical analysis claimed: need to assess whether bounds are tight and whether they
   predict empirical trends. If theoretical bounds don't match experiments, the theory is decorative.

## Calibrated assessment
Strong research direction but the distillation confound and inference gap are central
validity threats. Needs clear separation from BC/distillation baselines.
