# 07 — Tidy-up

Read before tidying up or redesigning existing code, and before assessing architecture. The design rules in [02](02-design.md) apply throughout.

Ask what you would build today if none of the current implementation existed, and what must be deleted to get there. An assessment stops after step 3 and reports. A request to tidy up or redesign is a request to change the code: carry out every step. For such a request, the smallest change that solves the problem is the one that reaches the target, not the smallest diff.

## Steps

1. **Understand.** Start from the named pain point or the strongest evidence: reported friction, recurring changes, tests that miss collaboration bugs. Trace representative behavior through callers, implementation, and tests, past the diff to the boundaries it touches, and keep the established domain terms. Separate required behavior and invariants from incidental structure. Existing interfaces and abstractions are hypotheses, not constraints; [contracts](10-project.md#contracts) are constraints.
2. **Derive the target.** Write down the fewest concepts and boundaries that meet today's requirements, and mark each current part kept, merged, replaced, or deleted. Examine the area through four lenses:
   - **Reuse:** what already exists and should be shared; which overlapping implementations collapse into one.
   - **Simplicity:** which concepts, states, branches, files, APIs, or steps can disappear; which [red flags](02-design.md#red-flags) appear.
   - **Efficiency:** unnecessary work, I/O, allocation, recomputation, or serialized steps with a practical cost. Skip speculative micro-optimization.
   - **Altitude:** whether the problem is solved at the right boundary, or workarounds pile up around a wrong model.

   When delegation is authorized ([05](05-delegation.md)), one agent per lens MAY review in parallel. Merge their findings into one target yourself; do not apply conflicting local suggestions one by one.
3. **Prioritize.** Rank by value: a removed failure mode, a removed parallel implementation, a simpler interface, less ongoing coordination. Drop cosmetic churn and any change whose maintenance or migration cost exceeds its benefit. For each candidate, record the affected files, the observed friction, the proposed change, the expected gain for callers and readers, the test impact, the cost, and your confidence. Separate supported recommendations from speculation.
4. **Implement end to end.** Before moving code, confirm that tests pin each required behavior and invariant from step 1, and add the missing ones; they are the check that fails if the redesign drops something. Move every caller, type, schema, test, configuration, and document to the target, and finish with one path, not old and new side by side. Delete dead code and tests of removed behavior; rewrite tests pinned to old internals ([01](01-testing.md#what-a-test-must-do)). Internal interfaces MAY break. A declared contract follows its compatibility policy, and destroying data or migrating live data needs authorization ([Autonomy](../AGENTS.md#autonomy)).
5. **Review again.** Confirm the whole is simpler, not only shorter: no scaffolding remains, and a maintainer who never saw the old design can follow it. In the report, put the target design and why it is simpler right after the goal, and list every changed contract with the caller updates made.
