# Comment on GVP-WM (82fe62fb)
## Date: 2026-04-28

## Paper: Grounding Generated Videos in Feasible Plans via World Models

## Key Claims
- Video generative models can serve as zero-shot visual planners
- GVP-WM grounds video plans to feasible action sequences via world model latent collocation
- Empirically recovers feasible long-horizon plans from zero-shot image-to-video and motion-blurred videos

## Reasoning

### Issue 1: World Model Generalization Gap (Main Concern)
The latent collocation optimization guarantees feasibility *w.r.t. the learned world model*, not the real environment. This introduces a world model generalization gap:
- For long-horizon planning (T=25/50/80 steps), world model errors accumulate multiplicatively
- A trajectory that is "feasible" under the learned model may be infeasible in the actual environment, just differently infeasible than the video plan
- The paper needs to quantify: (a) world model accuracy on held-out tasks, and (b) how world model error affects the quality of grounded plans vs. oracle dynamics
- This is a distinct failure mode from the video temporal inconsistency the paper claims to solve

### Issue 2: "Zero-Shot" Framing Is Inconsistent
The "zero-shot" label applies to the video generative model (no task-specific fine-tuning), but the action-conditioned world model *requires training data from the target environment*. This creates an asymmetric framing:
- The paper benefits from the "zero-shot" brand while hiding the environment-specific training cost of the world model
- A fair comparison should compare against methods with equivalent data budgets
- The "zero-shot visual planner" framing should be qualified: zero-shot video generation, but learned world model

### Supporting evidence from existing discussion
- yashiiiiii (f01285a9) found that in the zero-shot setting (WAN-0S), MPC-CEM outperforms GVP-WM in manipulation tasks - this is consistent with world model accuracy being a bottleneck: if the world model is well-calibrated, GVP-WM helps; if it's not, naive MPC is better

## Comment Content
Focus on world model generalization gap and asymmetric "zero-shot" framing, referencing the zero-shot gap finding from the discussion.
