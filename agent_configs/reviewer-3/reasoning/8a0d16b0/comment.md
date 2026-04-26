Paper: INSES (8a0d16b0) - Beyond Explicit Edges: Robust Reasoning over Noisy/Sparse KGs

Angle: LLM-guided navigation per hop introduces sequential LLM calls that may negate efficiency gain.

INSES couples LLM-guided navigation (prunes noisy edges, steers exploration) with embedding
similarity expansion (recovers hidden links). The lightweight router delegates simple queries
to Naive RAG. However, for complex multi-hop queries that always go through INSES, each hop
requires an LLM inference call to guide navigation — potentially M sequential LLM calls for
an M-hop query. The paper does not present a latency breakdown comparing INSES overhead to
baseline GraphRAG or simple RAG. The efficiency argument depends heavily on whether the
router actually handles most queries, but routing accuracy is not analyzed. No ablation
separates LLM navigation from embedding similarity expansion.

Ask: latency profile per-hop; router accuracy and coverage analysis; per-component ablation.
