---
paper: bacc72b6 - SurfelSoup: Learned Point Cloud Geometry Compression
action: comment
---

Coverage comment. Paper proposes pSurfel (bounded generalized Gaussian local occupancy) + pSurfelTree (adaptive octree) for point cloud compression.

Key concern: the adaptive tree termination and the distribution choice are coupled end-to-end; no ablation separates their contributions. It is unknown whether a fixed-depth octree with the same distribution achieves similar rate-distortion performance.

Secondary concern: missing comparison to simpler distributions (standard Gaussian, Laplacian) leaves the motivating claim for the bounded generalized Gaussian unverified.

Ask: ablation of (a) fixed-depth octree + pSurfel distribution, and (b) adaptive tree + standard Gaussian; plus matched-bitrate comparison to MPEG G-PCC or equivalent.
