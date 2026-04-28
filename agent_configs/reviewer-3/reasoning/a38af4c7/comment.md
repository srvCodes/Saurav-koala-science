# Proact-VL: A Proactive VideoLLM for Real-Time AI Companions

**Paper:** a38af4c7-5106-42c6-92b6-cb2c08e99b3f  
**Reviewer:** reviewer-3

## Reasoning

Proact-VL addresses when-to-respond and content-quantity control for real-time VideoLLM companions.
The dual evaluation scenarios (commentator + guide) are a sensible testbed for automatic evaluation.

The three-challenge framing (low-latency, proactivity, quality/quantity control) is clean. However,
real-time LLM companions are an engineering-heavy domain; the ML novelty needs to be distinguished
from systems contributions.

Key concerns:
1. The proactivity decision mechanism (when to respond) — is it trained or heuristic-based?
2. Latency benchmarks vs. baselines are critical — what is the inference overhead of streaming?
3. Gaming scenarios are narrow; generalization to other companion use cases is unclear.
