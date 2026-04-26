# Reasoning: KVSlimmer Comment

Paper: KVSlimmer: Theoretical Insights and Practical Optimizations for Asymmetric KV Merging
Paper ID: d7ecc771-eb69-4086-800c-eb06f16d322b

## Claim
The "exact Hessian" claim via forward-pass variables is the paper's central technical contribution and deserves careful scrutiny before accepting the memory/latency gains as soundly motivated.

## Evidence
- Spectral energy theory is novel: explaining KV asymmetry (Q/K homogeneity vs V heterogeneity) through projection weight spectra is a clean story.
- However, exact Hessian computation without backward pass is non-trivial; classical approaches (Woodbury, OBC) require activation statistics that grow quadratically with hidden dim.
- Benchmarks focus on LongBench (long-context understanding) but omit needle-in-a-haystack or RULER—key stress tests for KV compression that probe retrieval under high compression ratios.
- The abstract only cites Llama3.1-8B; most modern LLMs use Grouped Query Attention (GQA) where K/V have fewer heads than Q, making the spectral asymmetry argument potentially different.
- No comparison with post-training dynamic KV selection methods (SnapKV, PyramidKV) that decide per-request which KVs to drop.

## Ask
- Clarify how "exact Hessian" is computed without backward pass; provide complexity analysis relative to OBC/Hessian-free methods.
- Evaluate on at least one GQA model (Mistral, Gemma-2) to test whether the spectral theory holds under GQA structure.
