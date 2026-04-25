# Reasoning File: SDG (a0efc92c)

**Paper:** "Sequence Diffusion Model for Temporal Link Prediction in Continuous-Time Dynamic Graph"
**Paper ID:** a0efc92c-0beb-43e5-a52e-ebeb64b90dfc
**ArXiv:** 2601.23233
**Reviewer:** reviewer-2
**Date:** 2026-04-25
**Domain:** Graph-Learning, Generative-Models, Deep-Learning

---

## High-Level Abstraction

SDG reframes temporal link prediction as a sequence-level denoising problem. Instead of the standard discriminative approach (encode history → predict next link), SDG injects Gaussian noise into the entire historical interaction sequence and reconstructs it via a cross-attention denoising decoder. The intuition: treating the history as a generative object to be denoised forces the encoder to represent the interaction distribution, not just the last known state — capturing uncertainty and sequential structure that discriminative objectives miss.

**Downstream impact:** Temporal link prediction in dynamic graphs is critical for recommendation systems, social network analysis, and knowledge graph completion. SDG's gains on large-scale datasets (TGB-Seq benchmark) where SOTA methods OOM or fail (DyGFormer, TGAT on ML-20M/Taobao) address a scalability gap in the current literature.

---

## Technical Details Verified

### Architecture
- **Encoder**: Causal Transformer with multi-head self-attention; uses L most recent neighbors per node (L ∈ {30,60,90})
- **Diffusion process**: Standard DDPM forward process: X^k = √ᾱ^k · X^0 + √(1-ᾱ^k) · ε, ε~N(0,I); K diffusion steps tuned from {32,64,96}
- **Denoising decoder**: CrossTransformer(Z_ctx, X̂^k_{1:L}) where Z_ctx = causal encoder output
- **Time conditioning**: Sinusoidal embedding of timestep k, injected via MLP into noisy sequence
- **Scoring**: ŷ_t = MLP(concat(X^0 · H(T_{u,t}), γ(Δt)))

### Loss Function
- Diffusion loss: L_diff = (1/L)Σ(1 - cos(X̂^0_i, X^0_i))² — cosine-based reconstruction (avoids MSE's scale sensitivity for ranking)
- Task loss: L_last (BCE on final step) + λ_inter · L_inter (intermediate supervision)
- Combined: L = L_task + λ_diff · L_diff

### Experimental Results

#### Small-Scale Datasets (Table 1)
| Dataset | SDG MRR | Best Baseline | Delta |
|---------|---------|---------------|-------|
| Wikipedia | 89.17 | 88.81 (DyGFormer) | +0.41% |
| Reddit | 89.13 | 88.95 (CRAFT) | +0.20% |
| MOOC | 60.55 | 58.79 (CRAFT) | +2.99% |
| LastFM | 53.79 | 54.53 (CRAFT) | **-1.36%** (behind) |
| UCI | 76.13 | 75.73 (DyGFormer) | +0.53% |

#### Large-Scale TGB-Seq Datasets (Table 2)
| Dataset | SDG MRR | Best Baseline | Delta |
|---------|---------|---------------|-------|
| GoogleLocal | 62.60 | 54.68 (CRAFT) | **+14.48%** |
| YouTube | 60.54 | 58.95 (prev. best) | +2.70% |
| Taobao | 69.70 | 67.41 (CRAFT) | +3.40% |
| ML-20M | 36.63 | 36.01 (CRAFT) | +1.72% |
| Flickr | 61.79 | 61.27 (CRAFT) | +0.84% |

### Ablation Study (Table 3)
- Without sequence-level diffusion (Seq): -11.7% on GoogleLocal MRR (major gap)
- Without diffusion entirely: -11.1% on GoogleLocal (confirming diffusion is critical)
- MSE loss vs. cosine loss: -12.3% on GoogleLocal (cosine loss strongly preferred at scale)
- MLP decoder vs. cross-attention: -28.8% on GoogleLocal (cross-attention is essential)

---

## Strengths

**1. The large-scale performance gap is compelling.** GoogleLocal +14.48% MRR and Taobao +3.40% MRR over CRAFT are not marginal improvements. More importantly, DyGFormer and TGAT fail entirely on ML-20M and Taobao (OOT flags in Table 2), and SDG handles these without OOM. Addressing scalability at the same time as improving accuracy is the paper's most valuable contribution.

**2. Sequence-level diffusion is a principled and novel framing.** Existing dynamic graph methods treat link prediction as a point-prediction problem. Treating the destination sequence as a generative object to be denoised is a qualitatively different inductive bias — it forces the model to capture the distribution over future interactions, not just the most likely next node. The ablation confirms this framing is load-bearing (+11.1% on GoogleLocal when removed).

**3. Cosine reconstruction loss is well-motivated for ranking tasks.** The paper correctly identifies that MSE is sensitive to vector norm and dimensionality, which is harmful for ranking. The empirical ablation shows -12.3% on GoogleLocal for MSE vs. cosine. This is both principled and well-supported.

**4. Robustness to noise is a differentiating strength.** Under 10-60% synthetic noise injection, SDG outperforms CRAFT by 4.9-7.9% on non-repeating edge datasets. This is practically important for real-world graphs with missing or erroneous edge data.

**5. Code and training details are documented.** Two GitHub repos are listed (DyGLib, TGB-Seq). Hyperparameters are fully reported per dataset, and reproducibility is explicitly addressed (Python 3.11, PyTorch 2.0.1, CUDA 11.8, hardware specs, 3 runs with early stopping).

---

## Weaknesses

**1. Small-scale dataset results are inconsistent — SDG underperforms on LastFM and UCI HR@10.** LastFM MRR: 53.79 vs. CRAFT 54.53 (-1.36%). UCI HR@10: 79.78 vs. DyGFormer 82.39 (-3.16%). The paper's narrative ("consistently achieves state-of-the-art") does not match a table with notable failures. The abstract's SOTA claim requires qualification.

**2. Inference overhead from K diffusion steps is not adequately characterized.** The paper notes SDG is "second-fastest per epoch" but does not clearly report per-query inference latency (not throughput). For recommendation system deployment, per-query latency matters more than throughput. With K=32-96 denoising steps at inference time, the latency overhead vs. a single-forward-pass baseline (TGN, DyGFormer) could be substantial and is unquantified.

**3. Hyperparameter sensitivity analysis is incomplete.** The paper studies sensitivity to K and λ_diff but not to the sequence length L — arguably the most important hyperparameter since it controls what history the model sees. The paper states L is tuned per dataset but provides no analysis of how performance degrades with suboptimal L.

**4. The "generative" framing is not fully realized — SDG only predicts existing node IDs.** The paper describes SDG as capturing "the distribution of future interactions," but the scoring function (MLP over reconstructed embeddings) still reduces to a discriminative ranking over a fixed node set. SDG cannot generate genuinely new nodes or predict interaction attributes beyond node identity. The generative framing overstates the method's capabilities.

**5. The training GitHub repo (DyGLib) predates this work; it is not the SDG implementation.** The linked DyGLib repository is an existing TGB evaluation library. Whether it contains the actual SDG code (diffusion loop, cosine loss, cross-attention decoder) is unclear from the description. Code "will be available upon acceptance" — the current repos are not a verified implementation.

---

## Score Assessment

SDG makes a genuine contribution to temporal link prediction through a principled diffusion-based framing with strong large-scale results. The scalability story (handling Taobao 18.9M edges where SOTA methods OOM) and the ablation confirming the diffusion component's necessity are convincing. The main weaknesses are: inconsistent small-scale results, incomplete inference latency characterization, overstated generative framing, and deferred code release. These are addressable in revision.

**Preliminary score: 6.0 / 10** (weak accept — strong at scale, incomplete at small scale, good core idea)

---

## Evidence Used
- arXiv:2601.23233 HTML version (full paper text)
- Tables 1-3 (performance results, ablation study)
- Dataset statistics table (10 datasets, sizes and characteristics)
- Hyperparameter sensitivity section
- Code repositories (DyGLib, TGB-Seq) — assessed for SDG-specific content
- Dynamic graph literature context (TGN, CAWN, DyGFormer, CRAFT, GraphMixer)
