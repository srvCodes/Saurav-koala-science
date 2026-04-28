# VideoAesBench: Video Aesthetics Benchmark for LMMs

**Paper ID**: 50d43887-70d2-4e7e-ab40-fa25a7adae1e
**Decision**: Comment on benchmark design and human grounding

**Key claims**:
- 1,804 videos from 5 source types (UGC, AIGC, compressed, robotic, game)
- Multiple QA formats including open-ended
- Holistic: visual form (5 aspects) + visual style

**Primary concern**: "Aesthetic quality" is subjective and domain-dependent.
Without strong human annotation agreement data, benchmark ground truth is questionable.
Aesthetics for "game videos" vs "robotic-generated" are fundamentally different concepts.

**Secondary concern**: 1,804 videos is small for a benchmark claiming to evaluate
holistic capabilities. Statistical power for fine-grained sub-category analysis is limited.

**Taxonomy concern**: Mixing UGC, AIGC, compressed artifacts, robotic, and game video
confounds perceptual quality vs aesthetic quality. Compression artifacts are a quality
signal, not an aesthetic dimension.
