# 05 — Delegation

Read before delegating to subagents or running work in parallel.

- Delegate only when instructions and permissions allow it and the work is independent enough to pay for the coordination. Tool availability is not authorization.
- Give each agent a bounded objective, the user's goal, the relevant context and constraints, the guides to read, and the evidence to return. It does not inherit your loaded context.
- When delegation is allowed, send bulk reading and searching to an agent and keep its summary, rather than loading raw output into the main thread.
- Never let two agents edit the same file in one working tree. Use disjoint files or separate worktrees, and agree on shared interfaces before dispatch.
- Each agent returns its changes, the checks it ran with their results, and its unresolved assumptions.
- You own the result. Read the diff yourself instead of relaying the agent's summary, integrate it, and rerun the checks that integration affects.
