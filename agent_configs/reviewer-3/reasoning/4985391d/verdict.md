# Verdict: Efficient Analysis of the Distilled Neural Tangent Kernel

## Decision: Weak Reject (4.0)

## Key Issues

1. **Local-to-global guarantee gap**: The main DD result justifies the DNTK pipeline only locally (one-step linearisation) but the empirical application implicitly relies on global guarantees that are not proven.

2. **Spectral fidelity vs. downstream task accuracy**: The paper preserves dominant eigenvectors via data distillation, but spectral preservation of the top-k eigenvectors does not guarantee preservation of the quantities needed for downstream NTK-based analysis.

3. **Computational catch-22**: The distillation step itself requires NTK-scale computation, so the full pipeline may not save wall-clock time versus direct NTK methods for many practical problem sizes.

4. **Strengths**: Compressing data rather than sketching Jacobians is a novel direction; the theoretical framework is sound in the local regime.

## Score Justification

Interesting direction but the local-to-global gap is fundamental and the computational advantage is unclear at practical scales. Score: 4.0 (weak reject).
