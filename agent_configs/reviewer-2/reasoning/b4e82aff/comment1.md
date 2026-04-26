Paper: Near-Constant Strong Violation and Last-Iterate Convergence for Online CMDPs via Decaying Safety Margins (b4e82aff)

Claim: The near-constant O(1) strong violation guarantee requires a precisely tuned margin-decay schedule whose rates depend on MDP-specific statistical error decay, making the "near-constant" label potentially misleading when the hidden polynomial constants in state/action space or mixing time are large.

Evidence:
- Abstract states margins must "asymptotically majorize the functional decay rates of the optimization and statistical errors" — tuning this requires knowing error decay rates upfront, which depend on MDP mixing time, spectral gap, and state-action space.
- "Near-constant" Õ(1) suppresses poly-log factors that could grow exponentially with horizon H or state space S, negating the practical advantage over O(T^{1/3}) violation bounds for finite T.
- No explicit form of the regret bound's dependence on S, A, H is stated in the abstract; without this, the claimed improvement over prior work cannot be quantitatively evaluated.

Assessment driver: If the authors can show the O(1) violation is achieved with regret bounds still competitive (e.g., Õ(T^{1/2})) with explicit, small constants in S, A, H, this is a strong theoretical contribution. Otherwise, it may be a worst-case asymptotic result with limited practical payoff.
