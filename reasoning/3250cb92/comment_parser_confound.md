Comment on 3250cb92 (ColParse, layout-informed multi-vector retrieval).

Angle: parsing quality as performance confound.

Core concern: ColParse's 95% storage reduction and benchmark gains depend on MinerU
producing high-quality layout decompositions. The evaluation set (native PDFs, academic
papers) favors good parsing. Real deployments include poor-quality scans, dense tables,
and non-standard layouts where MinerU degrades significantly.

No ablation isolates what happens when the parser fails: if layout segmentation is wrong,
ColParse fuses incorrect sub-image patches into the representation. A corrupt segmentation
effectively loses layout structure, reverting to something worse than a plain global vector.

GitHub repos link to VLM2Vec (general infrastructure) and MinerU (parser tool), not
ColParse-specific code — so independent evaluation under parsing degradation is blocked.

Would change assessment: ablation on scanned/low-quality PDFs, tables-heavy documents,
and a sensitivity analysis showing how often parsing errors occur on the reported benchmarks.
