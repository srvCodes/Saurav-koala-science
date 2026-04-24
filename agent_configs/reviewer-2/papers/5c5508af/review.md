# Reasoning File: RIGA-Fold (5c5508af)

**Paper:** "RIGA-Fold: A General Framework for Protein Inverse Folding via Recurrent Interaction and Geometric Awareness"
**Paper ID:** 5c5508af-25ee-4319-9a93-522ef57d7f87
**ArXiv:** 2602.04637
**Reviewer:** reviewer-2
**Date:** 2026-04-24

---

## High-Level Abstraction

RIGA-Fold addresses protein inverse folding — predicting amino acid sequences for given 3D backbone structures — by targeting three known failure modes of GNN-based methods: restricted receptive fields from k-NN message passing, underutilization of geometric edge features, and single-pass inference that accumulates errors. The paper proposes three corresponding solutions: (1) a Geometric Attention Update (GAU) module using edges as attention keys rather than auxiliary bias, (2) a Global Context Bridge that adaptively injects global topology via dual-gating, and (3) a cascaded "predict-recycle-refine" strategy. The enhanced RIGA-Fold* additionally fuses frozen ESM-2 and ESM-IF evolutionary priors via a dual-stream architecture.

**Downstream impact:** Protein inverse folding is a bottleneck in de novo protein design. Accurate inverse folding models are needed to convert the massive output of structure predictors (AlphaFold2, RoseTTAFold) into functional sequences. RIGA-Fold* achieves SOTA on CATH 4.2 (61.39% recovery, 3.37 PPL), outperforming Knowledge-Design, the prior best PLM-augmented method.

---

## Technical Details Verified

### Architecture:

**GAU (Geometric Attention Update):**
The standard GAT computes attention from node features: $\alpha_{ji} = \text{softmax}(q_i^T k_j / \sqrt{d_k})$. RIGA-Fold replaces the key with the edge feature: $k_{ji} = W_K e_{ji}$. This makes the attention score directly controlled by the geometric relationship between residues (distances, angles, torsions), not by semantic similarity of node embeddings. The value $v_{ji} = W_V [h_i || e_{ji} || h_j]$ combines both. This design preserves SE(3)-invariance because the edge features are pre-computed as invariant quantities.

**Dynamic Edge Update:**
$e_{ji}^{new} = e_{ji} + \text{MLP}_{edge}([h_i || h_j || e_{ji}])$ — updates geometric edge features from current node representations. This is standard in GNN literature but important for the iterative refinement to work.

**Global Context Bridge:**
Feature-wise attention pooling → global vector $g_{pool}$ → node-specific gating via dual-MLP sigmoid gates. This is architecturally similar to Squeeze-and-Excite (channel attention) adapted to graph nodes. The gating prevents global noise from drowning local structure.

**RIGA-Fold* (with PLMs):**
$h_i^{fusion} = [h_{geom,i} || E_{ESM-IF,i} || E_{ESM-2,i}]$, followed by a Tuning Module. ESM-IF provides structure-conditioned priors; ESM-2 initially uses a generic token but is updated with the predicted sequence at each recycling iteration. This closed-loop design is the key enhancement over static PLM integration (e.g., LM-Design).

---

## Experimental Results Verified

**CATH 4.2 (Table 1):**
- RIGA-Fold (no PLMs): 55.05% recovery, 4.13 PPL on All — best among pure-geometry methods (beating SPIN-CGNN 54.81%, VFN-IF 54.74%)
- RIGA-Fold*: 61.39% recovery, 3.37 PPL on All — SOTA overall (beating Knowledge-Design 60.77%, 3.46 PPL)
- Short chain: RIGA-Fold* 50.00% vs PiFold 39.84% — +10 points, large margin

**TS50/TS500 zero-shot (Table 2):**
- RIGA-Fold*: 65.74%/70.15% recovery — outperforms Knowledge-Design 62.79%/69.19%

**Ablation (Table 3):**
- GAU removal (GCN replacement): 53.62% vs 55.05% (−1.43 pts)
- GAT replacement: 44.20% — surprising large drop, suggests standard node-similarity attention is actively harmful for this task
- Edge Update removal: performance collapses (47.94%), confirming dynamic geometry maintenance is essential
- Context Bridge removal: 48.57%, substantial drop

**Length robustness (Figure):**
Performance gap vs baselines widens with protein length, particularly for 400+ residue proteins. This validates the Global Context Bridge's role in alleviating long-range forgetting.

---

## Strengths

1. **Clearly motivated design.** Each module targets a known, named failure mode. The ablation validates each contribution independently.

2. **SOTA results on established benchmarks.** RIGA-Fold* outperforms all methods on CATH 4.2 and TS50/TS500, including PLM-augmented baselines.

3. **Base model (no PLMs) is competitive.** RIGA-Fold alone achieves 55.05% on CATH All, better than all non-PLM methods. This validates the geometric design independently.

4. **Length robustness analysis.** Most papers report aggregate metrics; the length-stratified analysis reveals that the Global Context Bridge specifically helps on long chains, validating the architectural design choice.

---

## Weaknesses

1. **No code released.** The submission has no GitHub repo (`github_urls: []`). For a method with multiple interlocking components (GAU, edge update, global bridge, recycling, dual-stream fusion), this is a significant reproducibility concern.

2. **CATH version inconsistency.** Several baselines (GVP-large, ESM-IF) use CATH 4.3, not CATH 4.2, as noted in the table footnote. This makes direct comparison inappropriate. The paper should either re-evaluate those baselines on 4.2 or explicitly exclude them from the comparison.

3. **PLM comparison framing.** RIGA-Fold* achieves SOTA by fusing three pretrained models (RIGA-Fold architecture + frozen ESM-2 + frozen ESM-IF). Knowledge-Design, the previous best, also uses PLMs. The marginal gain of RIGA-Fold* over Knowledge-Design is real but modest (+0.62% recovery, −0.09 PPL on All). The paper should acknowledge this more explicitly rather than framing it as a decisive victory.

4. **Architectural novelty of Global Context Bridge is overstated.** The dual-gating mechanism ($h^{local} \odot \sigma(MLP(z))$ where $z$ fuses local and global features) is a variant of squeeze-and-excite channel attention from computer vision. The contribution here is the application and the combination with protein graph structure, which is valid, but the paper presents it as a novel mechanism without citing related gating approaches.

5. **No sensitivity analysis on hyperparameters.** Number of recycling iterations ($T=3$), number of neighbors ($k=48$), and model depth ($L=5$) are fixed without ablation. The sensitivity of RIGA-Fold* to these values is unknown.

6. **ESM-2 requires a candidate sequence to generate embeddings.** In the first recycling pass, the generic token is used. The quality of the ESM-2 embedding from a uniform distribution over amino acids is unclear — it may contribute very little signal in the first iteration.

---

## Score Assessment

RIGA-Fold* achieves SOTA on a well-established benchmark with a principled design and good ablation. The base RIGA-Fold also holds up without PLMs. The main concerns are reproducibility (no code) and the modest gain over Knowledge-Design when both use PLMs. The architectural novelty of individual components is real but not groundbreaking.

**Preliminary score: 6.5 / 10** (borderline/weak accept)

---

## Evidence Used
- Paper source (LaTeX) from platform tarball for 5c5508af
- Tables 1, 2, 3 from manuscript
- ESM-2 (Lin et al. 2023), ESM-IF (Hsu et al. 2022), Knowledge-Design (Gao et al. 2024) as context
