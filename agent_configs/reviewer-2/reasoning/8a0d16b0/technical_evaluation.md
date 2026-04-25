# Reasoning File: INSES — Technical Evaluation (8a0d16b0)

**Paper:** "Beyond Explicit Edges: Robust Reasoning over Noisy and Sparse Knowledge Graphs"  
**Paper ID:** 8a0d16b0-17dd-469b-90b6-cb4110de705b  
**Reviewer:** reviewer-2  
**Date:** 2026-04-25  
**Domain:** Graph-Learning, NLP  

---

## High-Level Summary

INSES proposes a dynamic GraphRAG framework that couples LLM-guided navigation (noise pruning) with embedding-based similarity expansion (latent link recovery) for multi-hop reasoning over noisy/sparse knowledge graphs. The key insight is that KGs constructed from NLP tools are inevitably imperfect, and treating the graph structure as immutable during search is a fundamental limitation. A lightweight router further dispatches simple queries to naïve RAG and escalates complex multi-hop queries to INSES.

**Downstream impact:** GraphRAG is increasingly used in production RAG pipelines. A framework that makes graph-based reasoning robust to noisy/incomplete KGs — a universal property of real KGs — has wide applicability.

---

## Technical Details Verified

### Core Algorithm (INSES)
- Step 1: LLM extracts entities from query; matched to KG nodes via cosine similarity
- Step 2: LLM navigator prunes adjacent triples at each step, returning a "sufficient/insufficient" determination
- Step 3: Similarity expansion augments frontier with nodes above threshold τ_sim (cosine similarity)
- Iteration capped at 6 (small-world theory motivation)
- Router: classifies queries by complexity; easy → naïve RAG, complex/low-confidence → INSES

### Evaluation Datasets and Baselines
- **Benchmarks:** MuSiQue, 2WikiMultiHopQA, HotpotQA (1,000 sampled queries each)
- **Baselines:** GLM-4/GPT-4o direct, Naïve RAG (top-5/10), HyDE, IRCoT, GraphRAG (top-5/10), LightRAG, RAPTOR, SiReRAG
- **Metrics:** Exact Match (EM) and LLM-as-Judge
- **MINE benchmark:** 100 articles, 15 QA per article, evaluated across KGs built by KGGEN/GraphRAG/OpenIE

### Main Results (INSES+Router vs. best baseline SiReRAG)
- MuSiQue: EM 0.46 vs. 0.44 (+2%), LLM Judge 0.47 vs. 0.43 (+4%)
- 2Wiki: EM 0.67 vs. 0.50 (+17%), LLM Judge 0.71 vs. 0.53 (+18%)
- HotpotQA: EM 0.68 vs. 0.61 (+7%), LLM Judge 0.80 vs. 0.75 (+5%)

---

## Critical Analysis

### Missing Baselines: ThinkOnGraph (TOG/TOG2) and HippoRAG

The most directly relevant prior work — TOG (ThinkOnGraph, 2024) and TOG2 (2025), along with HippoRAG2 — is cited in the Related Work but absent from the main evaluation table. These methods perform LLM-guided traversal over KGs (TOG uses beam search; HippoRAG uses PPR-based retrieval). INSES's core claim is that LLM navigation + similarity expansion outperforms LLM-only navigation (as in TOG). Without a direct comparison to TOG on the same benchmarks and same KG construction procedure, it is impossible to attribute the gains to INSES's specific design choices rather than to any LLM-guided graph traversal approach.

The TOG paper itself reports 2Wiki results (using KGGEN or similar KGs) where it achieves competitive EM on the same datasets. An ablation (INSES without similarity expansion = effectively a TOG-style system) is shown in Table 3, confirming that LLM navigation alone provides +0.01–0.06 EM improvement. The key contribution (similarity expansion) adds +0.06–0.12 EM. A direct comparison to TOG — which also uses iterative LLM navigation — would clarify whether INSES's gains specifically stem from similarity expansion or from other implementation differences.

### Marginal Improvement on MuSiQue

On MuSiQue (the hardest benchmark), INSES outperforms SiReRAG by only 2 EM points. Since MuSiQue requires genuine multi-hop reasoning with explicit supporting facts, this narrow margin raises a question: is INSES's similarity expansion actually helping with the underlying inference task, or is it improving entity matching in sparser KGs? The MINE results (Figure 5) suggest the latter — the gains are largest for OpenIE KGs (+27%), which produce the noisiest, most fragmented entity nodes, while KGGEN KGs show only +5% improvement. This suggests INSES mainly helps with entity resolution/aliasing rather than multi-hop reasoning per se.

### Sampling Protocol and Statistical Significance

Experiments use 1,000 randomly sampled queries from each benchmark. No confidence intervals, p-values, or multiple-run means are reported. For EM scores, a 2% difference on 1,000 examples corresponds to a difference of ~20 correct answers — this could be within random sampling variability. Reporting standard deviations across sampling runs or performing significance tests would substantially strengthen the empirical claims.

### Sensitivity to τ_sim Threshold

The similarity threshold τ_sim is a critical hyperparameter: too low and spurious "virtual edges" introduce semantic drift; too high and the expansion fails to recover latent links. The paper does not report the value of τ_sim, how it was selected, or an ablation over it. This matters because the optimal τ_sim likely varies across KG construction methods (KGGEN vs. OpenIE produce very different embedding distributions).

### Presentational Issue: Commented-Out Text

The LaTeX source contains multiple large comment blocks — including an entire alternative Introduction (the original Introduction is fully duplicated in `\begin{comment}...\end{comment}`). This is unusual for a polished submission and suggests the paper went through a significant restructuring without cleanup. While not a technical flaw, it raises questions about completeness.

---

## Overall Assessment

INSES addresses a genuine limitation of GraphRAG and proposes a sound engineering solution. The MINE results convincingly show robustness across KG construction methods. The 2Wiki results are the most compelling, showing a 17% EM improvement. However, the absence of TOG/HippoRAG from the comparison table, the marginal gains on MuSiQue, and the lack of statistical rigor weaken the empirical case.

**Score: 5.0 / 10** (borderline — technically sound with real contributions but evaluation has significant gaps)

---

## Evidence

- Paper source (LaTeX tarball 8a0d16b0)  
- Main results table (Table 2: EM and LLM Judge on three benchmarks)  
- Ablation table (Table 3: component contributions)  
- MINE benchmark analysis (Figure 4, Section 4.4)  
- Related work: TOG (thinkongraph2024, thinkongraph2025), HippoRAG (gutierrez2024hipporag, gutierrezrag2025hipporag2)  
