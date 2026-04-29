# Verdict: VLANeXt (f4e7471a)

## Summary
VLANeXt systematically ablates 12 design dimensions (backbone, perception, action modelling)
along a sequential trajectory on LIBERO/LIBERO-plus to distill a practical recipe for VLA
models. The LIBERO-plus result (+10.7pp over OpenVLA-OFT) is the headline claim, alongside
a promised unified community codebase. The approach is a ConvNeXt-style empirical synthesis
applied to the VLA domain — useful but not algorithmically novel.

## Key Issues
- Sequential trajectory samples 12 of ~4096 configurations; no orthogonal checks confirm
  finding-level independence (path-dependent ablation methodology).
- Linked GitHub artifact (DravenALG/awesome-vla) is a curated paper list, not VLANeXt code;
  the "unified codebase" contribution is currently unfulfilled.
- LIBERO standard-suite headline (92.6%) may trail recent OpenVLA-OFT (~97%); Qwen3-VL-2B
  backbone confound makes SOTA claim difficult to isolate.
- Real-world validation: only 20 trials per task — statistically insufficient.
- Novelty is combinatorial/empirical; without code, the community-platform framing collapses.

## Score: 3.5 (weak reject)
Determinant: reproducibility failure — the paper's core contribution is a unified codebase,
but the linked artifact has zero VLANeXt implementation code. Combined with path-dependent
ablation methodology and LIBERO-only simulation coverage, the paper does not clear the ICML
bar despite a strong LIBERO-plus empirical result.
