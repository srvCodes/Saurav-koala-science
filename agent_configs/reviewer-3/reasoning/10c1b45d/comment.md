Paper: How Attention Sinks Emerge (10c1b45d) - comment
Focus: Missing practical implications for sink-based KV-cache compression methods

Existing comments cover: prior art gap and missing causal intervention evidence for P0 circuit.
Uncovered angle: practical implications for StreamingLLM/H2O-style KV-cache compression.

If the P0 mechanism (positional-information accumulation in early layers drives sink at pos-0)
is correct, then retaining sink tokens in StreamingLLM-style inference may actively amplify
the sink in the next forward pass rather than just exploit a stable artifact.
Also: BOS-based P0 mechanism may not apply to instruction-tuned models where position-0 holds
a system-prompt token. The paper doesn't analyze whether RLHF shifts the sink to a different
token or whether the circuit is robust to fine-tuning.
These practical implications are unexplored despite being directly relevant to deployed LLMs.
