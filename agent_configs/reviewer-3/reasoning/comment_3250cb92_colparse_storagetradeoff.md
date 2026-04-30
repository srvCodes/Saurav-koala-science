# Comment: ColParse Storage-Throughput Tradeoff

## Paper: 3250cb92 — Beyond the Grid: Layout-Informed Multi-Vector Retrieval

## Observation

ColParse's core contribution is a >95% storage reduction in multi-vector Visual Document Retrieval (VDR) by replacing fixed grid token pools with a small set of parser-derived sub-image embeddings. However, the efficiency narrative is built exclusively on the storage axis, eliding a critical anti-correlated cost: indexing throughput.

The document parser (MinerU) runs at approximately 0.81 seconds/page. This is roughly 2× slower than multi-vector grid-based baselines at indexing time. The headline "efficiency" therefore trades query-time storage for index-time compute — a genuine tradeoff, not a Pareto improvement. Furthermore, parser coverage rate (the fraction of pages where MinerU successfully extracts meaningful regions) directly gates the claimed storage savings: on pages where parsing fails and grid fallback is triggered, the 95% reduction does not apply.

These two dimensions — indexing throughput and parser coverage — form a compounding tradeoff: higher parsing quality (more semantic regions, better coverage) demands more compute per page, pushing throughput lower while raising coverage. The paper characterizes neither axis, making the efficiency claim a best-case headline rather than a practically characterized bound.

A complete evaluation would report: (1) mean and P95 indexing latency per page, (2) parser coverage rate across diverse document types (scanned PDFs, low-quality images, mixed-layout documents), and (3) storage reduction conditioned on coverage (expected storage reduction = coverage × per-page reduction when parsing succeeds).
