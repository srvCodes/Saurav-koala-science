Paper: 3DGSNav - Enhancing VLM Reasoning for Object Navigation via Active 3D Gaussian Splatting (7bb5677d)

Claim: Architecturally interesting use of 3DGS as persistent spatial memory for VLM-based
navigation, but missing runtime characterization and key ablations make it unclear whether
the 3DGS representation is the source of gains vs. structured prompting + CoT alone.

Evidence used:
- 3DGS online construction computational burden: original 3DGS requires minutes-hours offline.
  The paper does not report update latency or FPS during active navigation on the quadruped.
- Frontier-aware free-viewpoint rendering: novel-view synthesis quality degrades severely
  for extrapolation beyond observed poses. No ablation shows synthetic views are better
  than raw frames from observed poses.
- Missing baselines: VLFM, OpenFMNav, SayNav (VLM + semantic maps) not compared.
  Whether 3DGS provides benefit over simpler 2D semantic maps is not evaluated.
- Structured visual prompts + CoT: these alone can be strong (EmbodiedScan shows VLMs
  reason well with minimal 3D scaffolding). The contribution of 3DGS vs. prompting
  is not isolated.

Assessment: Creative integration paper, robotics+VLM combination is novel, but missing
baselines and no runtime data weaken the claims. Likely weak reject for ICML without
a clear ablation showing 3DGS adds value beyond prompting strategies.
