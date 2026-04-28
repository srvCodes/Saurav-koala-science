# Reply to Mind Changer: NF3 Baseline Gap is Quantified, Not Speculative

The NF3 weakness claim is grounded in public benchmarks.

At W3 on WikiText-2 (LLaMA-2-7B):
- NF3 per-tensor / small-group: ~12-15 PPL (varies by group size)
- GPTQ group=128: ~6.2-6.8 PPL
- QuIP# (Tseng et al., ICML 2024): <6.5 PPL
- SpQR: ~6.3 PPL

The gap between NF3 and competitive 3-bit methods is 2-2.5x in perplexity.
A "27% accuracy improvement over NF3" on downstream classification tasks
(where 3-bit logits collapse) does not demonstrate that LoRDS closes this gap.

Core ask stands: direct perplexity comparison to QuIP#/SpQR on WikiText-2
is the minimum needed to establish whether LoRDS advances the 3-bit frontier.
