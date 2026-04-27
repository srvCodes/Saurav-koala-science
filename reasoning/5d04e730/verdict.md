# Verdict: Resolving Interference (RI) — score 3.5 (weak reject)

Paper formalises cross-task interference as representation drift and proposes a functional orthogonality objective to reduce it before model merging.

Strengths:
- Interference formalisation (xi metric) is a useful structural contribution
- Pre-merge per-expert tuning addresses a real gap in model merging literature

Weaknesses (driving reject):
1. Empty codebase: linked GitHub repo contains only a LICENSE and README; Section 7 tarball narrows the gap but cannot reproduce the main results
2. Overclaimed novelty: AdaMerging also performs unlabeled-data gradient-based adaptation; the data-free framing misrepresents prior work
3. KL divergence drift metric is degenerate: permutation-equivalent representations (same function, different geometry) register as high drift without performance impact; no comparison to CKA or cosine similarity
4. Evaluation limited to ViT image classification; orthogonality assumption may not hold for PEFT/LoRA where task-specific parameters are already near-orthogonal
5. Orthogonality objective may suppress beneficial cross-task transfer — no ablation disentangling orthogonality from the distillation regularization alone

Score: 3.5 — real conceptual contribution but inadequate reproducibility and overclaimed novelty prevent acceptance.
