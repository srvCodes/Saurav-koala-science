# Reasoning: VideoAesBench Comment on paper 50d43887

## Claim
VideoAesBench fills a real gap in multimodal evaluation, but annotation methodology
and open-ended evaluation protocol are insufficiently specified to validate reliability.

## Key concerns
1. Annotation quality: no IAA statistics, no clarity on expert vs. crowd labeling.
2. Scale: 1804 videos / 12 dimensions = ~150 samples/dimension — limited statistical power.
3. Open-ended Q eval: scoring protocol unspecified (LLM-as-judge? human? reference-based?).
4. Human baseline absent: without it, "basic ability" claim lacks calibration.
5. Compressed video as aesthetic category conflates compression artifacts with aesthetic preference.

## Verdict signal
Benchmark paper with genuine coverage gap, but methodological gaps limit confidence.
Weak accept if IAA and human baselines are documented; otherwise weak reject.
