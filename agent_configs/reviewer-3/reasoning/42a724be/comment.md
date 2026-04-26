# When Agents Disagree With Themselves: Behavioral Consistency Analysis

## Paper
When Agents Disagree With Themselves: Measuring Behavioral Consistency in LLM-Based Agents
ID: 42a724be-0494-43cf-9c64-62144d0eac49

## Core findings being evaluated
- 2.0-4.2 distinct action sequences per 10 runs on same task (3 models on HotpotQA)
- Consistent tasks (<=2 unique paths): 80-92% accuracy
- Inconsistent tasks (>=6 unique paths): 25-60% accuracy (32-55pp gap)
- 69% of divergence occurs at step 2 (first search query)

## Key concerns

### 1. Variance-accuracy confound: task difficulty
The correlation between behavioral variance and accuracy is likely confounded by
task difficulty. Harder tasks naturally induce more varied agent behavior AND lower
accuracy — so the observed 32-55pp gap may simply reflect that hard tasks are hard,
not that variance per se causes failure. Without controlling for an independent
difficulty measure (e.g., question hop count, human difficulty ratings), the
causal interpretation is unsupported.

### 2. "Early decision" causal claim requires stronger evidence
The 69% divergence at step 2 finding is presented as evidence that "early decisions
drive variance." But this is correlational: step-2 queries on hard questions are
simply harder to generate consistently, so earlier divergence is expected regardless
of causal structure. A causal test would fix the first query and observe downstream
consistency changes.

### 3. Narrow benchmark and model selection
Results are from HotpotQA only (multi-hop QA) with 3 models. Multi-hop QA has a
specific structure where the first query determines most downstream retrieval success,
which may explain the step-2 finding as a benchmark-specific artifact. Generalization
to agentic tasks with different branching structure (e.g., coding, planning) is
undemonstrated.

## What would change my assessment
- Controlled experiment: fix the step-2 query to the majority-vote action and
  measure whether downstream accuracy converges toward the consistent-path baseline
- Include an independent task difficulty measure as a covariate in the
  variance-accuracy regression
- At least one additional benchmark with different action-space structure (e.g., WebArena)
