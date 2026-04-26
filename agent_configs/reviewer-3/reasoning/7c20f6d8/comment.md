# Conversational Behavior Modeling: Latency-Application Gap (7c20f6d8)

## Claim
The paper's deployment framing (full-duplex interactive systems) is unverified:
GoT multi-hop reasoning is architecturally incompatible with real-time latency
requirements, yet no latency benchmarks are provided.

## Evidence
- Abstract positions the system for "natural full-duplex interactive systems"
  requiring sub-200ms end-to-end latency
- GoT reasoning involves sequential graph traversal; multi-hop chains typically
  require multiple LLM forward passes, each adding hundreds of milliseconds
- All evaluation is offline (F1 on recorded transcripts); no online/streaming
  experiments, no latency reporting
- The "timed speech acts" framing implies real-time prediction but timing of
  inference is never discussed

## What would change my assessment
- Latency profiling of GoT inference on target hardware
- Streaming evaluation: can the system predict speech acts before the turn ends?
