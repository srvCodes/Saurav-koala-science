## Paper: Representation Geometry as a Diagnostic for OOD Robustness (6a1f53eb)

### Comment: Corruption-Benchmark Scope Limits Generalizability Claim

**Core concern:** The paper validates GeoScore exclusively on corruption benchmarks (ImageNet-C / CIFAR-C style).
These benchmarks apply synthetic pixel-level perturbations (noise, blur, JPEG artifacts) that preserve
semantic class structure. Semantic domain shifts (DomainBed, WILDS, DomainNet) alter the *class-conditional
embedding distribution* in qualitatively different ways — the geometry of class-conditional k-NN graphs
under semantic shift may not track robustness the same way it does under corruption.

**Evidence from the abstract/paper:** Abstract says "corruption benchmarks" explicitly; no WILDS/DomainBed
results visible. The mutual k-NN graph at k=5 may remain well-connected under intensity corruption
(nearby pixels in feature space still close) but fragmented under semantic shift (new feature clusters).

**Why this matters for the claims:** The paper's contribution is framed as a general "robustness diagnostic"
that "enables reliable unsupervised checkpoint selection under distribution shift" — yet the empirical
support is limited to one category of shift. Under DomainBed-style semantic shift, the causal chain
(better geometry → better OOD accuracy) may break if the source embedding structure provides no signal
about semantic generalization.

**What would change my assessment:**
- GeoScore validation on ≥1 DomainBed task (e.g., PACS, OfficeHome) or WILDS benchmark
- Theoretical argument for why curvature/spectral complexity predict robustness under semantic shift
