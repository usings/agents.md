# Design

Read when designing or changing an interface, ownership, state model, or architecture. Start from today's confirmed requirements, not from the current file layout.

## Choose boundaries

- Identify the actors, domain vocabulary, invariants, and actual contracts. Distinguish required behavior from incidental structure. Write representative caller examples, including failures, when changing an interface.
- Compare credible alternatives when a consequential choice remains uncertain; use a focused prototype to resolve the deciding assumption. A small local change does not need a design exercise.
- Give each business decision and mutable state a clear owner. Group what changes for the same reason; isolate responsibilities that change independently.
- Prefer interfaces that hide useful complexity. An interface includes ordering, errors, configuration, and performance constraints, not just signatures. If removing a layer eliminates only forwarding, consider removing it; retain adapters that enforce a real boundary or policy.
- Prefer a direct implementation over speculative configuration, registries, and frameworks. Do not merge unrelated concepts merely because their code looks alike. Judge simplicity by what callers and maintainers must understand, not line count.

## Model state and effects

- Give meaningful alternatives explicit representations. Distinguish missing, unknown, invalid, and empty when the domain does. Put invariants at an owner that can enforce them rather than scattering defensive checks through consumers.
- Validate untrusted inputs at their boundary and preserve the established invariants inside it. Types do not replace runtime checks for external values or guarantees affected by concurrent mutation.
- Separate domain decisions from I/O when it makes those decisions independently understandable and testable; do not create pass-through layers just to enforce a diagram.
- Prefer isolated state when actors do not need to share it. Where they do, specify ownership and conflict behavior and enforce it through transactions, locking, compare-and-swap, or another appropriate mechanism.
- Distinguish a new business operation from a retry of the same operation. Two distinct increments may both apply, while duplicate delivery of one increment may need deduplication. Define operation identity and the atomic boundary when that distinction matters.
- For multi-step state changes, define partial completion and recovery. Test relevant interruption points; do not claim atomicity or exactly-once effects without a mechanism. Temporary state must have a safe ownership and recovery rule.

## Deliver the target

- Ask what would exist if the requirement had been present from the start. Keep, merge, replace, or remove current parts according to their value, not their age.
- Migrate internal callers and delete superseded paths in the same change. A staged transition needs a real rollout constraint, an owner, and an exit condition.
- For external contracts or persisted data, identify consumers and versions that must coexist. Specify compatibility, deliberate rejection, and rollback or safe roll-forward as appropriate to the authorized change.
- Deliver verifiable increments toward one coherent design. Reconsider the target when evidence invalidates an assumption; do not defend sunk implementation cost.
