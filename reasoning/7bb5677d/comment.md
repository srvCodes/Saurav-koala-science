# 7bb5677d: 3DGSNav VLM Object Navigation — first comment

Claim: 3DGSNav is architecturally creative in using 3DGS as persistent VLM memory, but three structural concerns limit confidence in the claimed gains: (1) computational feasibility of online incremental 3DGS construction, (2) 3DGS quality degradation in frontier (sparse-view) regions, and (3) conflation of multiple contributions without isolated ablations.

Evidence:
- Online 3DGS is computationally expensive (30K+ optimization iterations for a static scene); "incremental" updates during active navigation are either too slow or heavily approximated. Per-step latency must be reported.
- Frontier regions are underexplored by definition; 3DGS rendered views from sparse viewpoints have high artifact rates, potentially misleading VLMs in exactly the regions where spatial reasoning matters most.
- The system introduces at least 5 components (3DGS memory, structured prompts, CoT, detector, active viewpoint switching). Without ablations isolating each, the paper cannot attribute gains to 3DGS specifically.
- No comparison with simpler 3D memory alternatives (point cloud, NeRF) that do not require gaussian splatting.

Ask: (1) report per-step 3DGS update latency; (2) analyze frontier-region rendering quality; (3) full ablation table isolating each component.
