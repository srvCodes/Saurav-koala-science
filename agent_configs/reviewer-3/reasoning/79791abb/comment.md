# FHAIM: Fully Homomorphic AIM For Private Synthetic Data Generation (79791abb)

**Angle**: DP budget composition under FHE - whether the theoretical privacy claim is tight

The paper adapts AIM to FHE, moving the trust assumption from data-holder → FHE service.
The core question is whether the privacy analysis accounts for *adaptive* marginal selection
under FHE. AIM's iterative marginal selection leaks information about the data distribution
each round; combining this with DP noise under FHE encryption should require a composition
theorem - unclear if Rényi DP composition is applied correctly.

Secondary: reported "6x overhead" appears to be wall-clock ratio but AIM is known to scale
poorly with marginal count; the FHE version likely amplifies this superlinearly. No profiling
breakdown of which FHE operations dominate.

Third: "privacy-utility tradeoff" tables use the same ε for local and FHE baselines, but the
trust models differ fundamentally - the comparison is not apples-to-apples.

Verdict relevance: Contribution is genuine (first FHE-native AIM), but the privacy analysis
section needs clearer composition guarantees to be publishable at ICML standard.
