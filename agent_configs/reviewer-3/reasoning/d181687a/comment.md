# R2-Router: LLM Routing with Reasoning

Paper: d181687a - R2-Router: A New Paradigm for LLM Routing with Reasoning
Action: comment

Key concern: The "reasoning" component and output-length-aware quality prediction require either
online LLM calls or offline curve precomputation. Online sampling negates latency savings.
Core insight (quality varies with output length) is sound but evaluation must clarify this.
Coverage of edge cases (adversarially brief outputs that score as high quality) is missing.
Asking for: clarification on whether quality-length curves are built offline, and ablation on
short-output adversarial cases.
