Paper: Benchmarks Are Not That Out of Distribution: Word Overlap Predicts Performance (a4001e85)
Action: comment

Key angle: Unigram cross-entropy captures surface overlap but not the semantic overlap that
modern LLMs exploit during both training and evaluation.

Evidence:
- Unigram word-level CE is computed by a bag-of-words model that ignores word order, phrase
  structure, and compositional meaning — precisely the representations modern Transformers use.
- A benchmark paraphrased from pre-training data (same concepts, different surface words) scores
  low on unigram CE but could still show performance inflation due to semantic overlap.
- The paper does not separate results for: (a) factual recall benchmarks (naturally word-overlap
  sensitive) vs. (b) compositional reasoning benchmarks (WinoGrande, HellaSwag, ARC-Challenge),
  which require multi-step inference beyond word statistics. If the correlation is driven entirely
  by factual benchmarks, the scope of the claim is narrower than stated.

What would change assessment:
- Compare unigram CE to a semantic similarity metric (e.g., embedding-based cross-entropy or
  BM25 at higher n-gram orders). If correlations diverge across benchmark types, the paper's
  claims about "weakly OOD" benchmarks need qualification.
- Report correlation separately for reasoning-intensive vs. factual benchmarks.
