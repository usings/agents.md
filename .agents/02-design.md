# 02 — Design

Read before designing an interface, module boundary, data model, or state, and before refactoring one. To tidy up, redesign, or assess existing code, read [07](07-tidyup.md) as well.

## Modules

- A module is anything with an interface and an implementation: a function, file, package, or feature slice. Its interface is everything a caller must know: types, invariants, ordering, errors, configuration, and performance limits.
- Prefer deep modules: substantial behavior behind a small interface. Judge depth by the complexity removed from callers, not by size.
- Deletion test: if deleting a module removes only forwarding, delete it. If complexity would spread into its callers, it earns its place.
- Reader-load test: a new reader can quickly answer "where does X come from?" and "what can change X?". If not, cut layers to trace or hidden and mutable state to hold.
- For a public interface change, write representative caller code first (defaults, overrides, failures) and keep it as the acceptance cases.

## Red flags

Revise a design that shows any of these:

- **Pass-through layer.** It forwards the same arguments to the same shape.
- **Leaked decision.** A representation, policy, or wire type appears in more than one module, so one change needs coordinated edits.
- **Temporal decomposition.** Modules named after steps (load, validate, save) each repeat the same rules.
- **Split ownership.** More than one module writes the same state.
- **Two ways to do one task.** Callers copy whichever they find first. Keep one and delete the other.
- **Hand-synced lists.** Derive them from one source, or make the build fail when they disagree.
- **Branch growth.** A new feature adds one more branch to an existing chain, or a second flag must stay in sync with the first. Use a state machine, discriminated union, table, or registry.
- **Permanent wrapper.** An adapter exists to hide an interface whose names or shape mislead. Change the interface and migrate its callers.
- **Forced generality.** Unrelated concepts share a framework, base class, or generic helper only to remove duplication. Keep the local duplication; compose small pieces instead.

## Data and boundaries

- Parse external input (network, files, arguments, environment, database rows) into domain types once, where it enters. Inside, trust the types and do not revalidate.
- Give distinct meanings distinct types even when they share a primitive. Derive types from the authoritative schema when one exists. Do not silence the compiler.
- Keep business rules in pure functions. Keep framework and I/O code thin.

## Failure modes

Answer these for each operation that changes state, before implementing it:

- What happens if it runs twice, or after a crash at any point? It MUST converge to the same end state, and anything it leaves behind (a lock, a temporary file, a half-written record) MUST be recognizable as stale.
- Can two actors write the same file, key, or object? First give each its own. Serialize structurally (single writer, lock, compare-and-swap) only when one shared target is a real invariant.
- What do old data, old clients, and half-finished migrations see? Test them when compatibility is required; test the deliberate rejection when it is not.
- Which inputs can each producer actually send: absent, empty, malformed, oversized, duplicated, out of order?
