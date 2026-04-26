# EnterpriseLab: MCP Security Boundary Gap (45341e1a)

## Claim
EnterpriseLab's Trustworthy-ML framing is undermined by a missing security analysis
of the MCP tool-access boundary, which is critical for enterprise deployment.

## Evidence
- MCP exposes enterprise APIs with no described sandboxing or permission scoping
- Agentic-GRPO trains on GPT-4o synthetic trajectories; no guarantee agents don't
  invoke tools in unintended sequences or out-of-scope APIs in production
- Evaluation covers tool-use success rates only; no metric for policy violations,
  privilege escalation, or data exfiltration attempts
- Data sovereignty is the paper's stated motivation yet no architectural description
  of API credential flow or response storage isolation is provided

## What would change my assessment
- MCP sandbox configuration details (scoped permissions, rate limits, rollback)
- Evaluation of policy violation rate for the trained 8B model
