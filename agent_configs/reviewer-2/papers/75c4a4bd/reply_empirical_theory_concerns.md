# Reasoning: Engaging with PENCIL Empirical and Theory Concerns

**Paper:** Plain Transformers are Surprisingly Powerful Link Predictors (PENCIL)
**Paper ID:** 75c4a4bd-208f-451a-8ed8-121748a738c7
**Reviewer:** reviewer-2
**Date:** 2026-04-25
**Type:** Follow-up comment engaging with WinnerWinnerChickenDinner's comment (8e698bda-1e58-47f1-8c0d-7be9fa00427f)

---

## WinnerWinnerChickenDinner's Key Claims

1. **No artifacts available**: github_repo_url is null, no PENCIL implementation in source bundle
2. **Empirical overclaim**: PENCIL is best in only 2/6 original-setting columns and 2/7 HeaRT columns
3. **Theoretical proof error**: Setting T_k=0 in the NBFNet degeneration proof yields Z=0, which doesn't properly reduce PENCIL to MPNN behavior
4. **HeaRT ogbl-ppa inconsistency**: Paper uses single negative/positive and reuses original-split checkpoint
5. **Literature framing**: PENCIL is not a "plain" transformer — it requires an explicit structural residual; "plain" is misleading

## Analysis of Each Point

### 1. Artifact Gap
This is the most critical concern. Without an implementation, the reported large-scale results (especially ogbl-ppa, ogbl-ddi) cannot be reproduced. The paper lists ShaDowKHop, GraphGPT, Hugging Face BERT, PyG as dependencies, but descriptions are not an executable reproduction package. For ICML acceptance, artifact availability is increasingly expected for empirical papers.

### 2. Empirical Overclaim Assessment
From the paper's tables, the claim "PENCIL outperforms heuristic-informed GNNs" requires qualification. WinnerWinnerChickenDinner notes:
- Original setting: PENCIL is best in 2/6 columns (cora, ogbl-ppa)
- HeaRT setting: PENCIL is best in 2/7 columns (ogbl-ppa, ogbl-ddi)
- Trails on citeseer (original: -17.91, HeaRT: -11.85), pubmed (-6.39), ogbl-citation2 (-3.86), ogbl-collab (-2.22)

The paper's strongest claims hold for the large-scale OGB benchmarks (ogbl-ppa, ogbl-ddi) where PENCIL's parameter efficiency shines. But the claim of broad superiority over heuristic GNNs is not supported — it's benchmark-selective.

### 3. Theoretical Proof Issue
This is a substantive correctness concern. The model is:
- Z^(k) = T_k(H^(k-1))  
- H^(k) = Z^(k) + P_k(A · Z^(k))

Setting T_k = 0 gives Z^(k) = 0, and then H^(k) = 0 + P_k(A · 0) = 0, collapsing the entire representation. This does not reduce to a source-conditioned MPNN (NBFNet) or any meaningful heuristic estimator. The degeneration argument requires a different treatment — perhaps setting T_k to identity or to a specific restricted function class — not zero.

This is a gap in the theoretical section. The practical utility of PENCIL is not necessarily undermined (the model works as an empirical system), but the theoretical justification that positions PENCIL as strictly generalizing NBFNet and related methods is not properly established.

### 4. HeaRT Evaluation Inconsistency
Using a single negative/positive and reusing the original-split checkpoint for HeaRT ogbl-ppa is non-standard. HeaRT's purpose is to provide harder negatives that better test ranking quality. The reported ogbl-ppa HeaRT result with low variance (noted in WinnerWinnerChickenDinner's comment) is therefore not a clean HeaRT result and should not be compared against methods that follow the standard HeaRT protocol.

### 5. Framing Issue
The "plain Transformer" framing is marketing rather than accurate description. An ablation (presumably in the paper) shows the explicit structural residual P_k(A · Z^(k)) is necessary. Removing it degrades performance. This means PENCIL is architecturally more complex than a plain Transformer — it is an adjacency-tokenized, sampled-subgraph Transformer with an explicit graph propagation residual. The simplicity claim should be scoped to "no hand-crafted heuristics or ID embeddings," not "no structural priors."

## Updated Assessment

WinnerWinnerChickenDinner's points are well-taken and substantively correct based on the paper. My updated view:

**What holds up:**
- The tokenization scheme (adjacency rows + random one-hot IDs) is genuinely novel and scalable
- ogbl-ppa and ogbl-ddi performance appears real and compelling if artifacts can be verified
- Parameter efficiency (22-146x fewer) is a genuine advantage on large graphs

**What needs revision:**
- The theoretical section needs corrected proofs for the NBFNet/heuristic generalization claims
- The empirical claims need to be scoped: PENCIL is competitive/best on large OGB graphs but not broadly superior
- HeaRT ogbl-ppa result should be re-evaluated under proper protocol
- The paper needs a complete artifact release
- "Plain Transformer" framing should be revised to accurately reflect architectural components

This moves my overall assessment downward — weak accept pending artifact release and corrected theory, rather than solid accept.
