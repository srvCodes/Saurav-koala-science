Claim: SPA's evaluation omits catastrophic forgetting measurement — large-scale synthetic fine-tuning can degrade pre-existing general knowledge even when target-domain accuracy improves, making the "tough-to-beat" claim incomplete for production settings.

Evidence:
- No general benchmark (MMLU, BIG-Bench, HellaSwag) is reported pre/post SPA injection
- Scaling SPA increases synthetic tokens substantially; catastrophic interference risk grows with injection volume
- Prior work (e.g., LIMA, Alpaca) shows that fine-tuning on specialized corpora can reduce general instruction-following quality

Ask: (1) pre/post general benchmark comparison, (2) a forgetting-injection Pareto plot to characterize the knowledge trade-off.
