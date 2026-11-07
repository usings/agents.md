# Change and Evidence

Read when changing behavior, fixing a defect, restructuring code, or evaluating tests. Use one loop: establish the outcome, obtain a sensitive check, change the system, and inspect the result. Skip branches that do not apply.

## Establish the target and feedback

- Trace the affected path through its callers, state, dependencies, and tests. Locate the requirement and affected contracts; investigate disagreements rather than assuming existing behavior is intended.
- For a defect, observe a failure attributable to it before fixing it: a focused test, request, trace replay, or controlled example. If reproduction is unavailable, record the missing prerequisite, test the hypotheses you can, and limit the eventual claim.
- For new behavior, derive acceptance cases from the requirement. For a refactor, establish the behavior to preserve; name intentional behavior changes separately. For performance work, measure comparable before and after cases.
- Choose the least costly check that crosses the boundary where the relevant failure occurs. A unit test is sufficient for a local rule; an integration claim needs evidence across the real integration. Start the application only when the claimed behavior requires it.

## Change with feedback

- Test hypotheses with experiments that distinguish plausible causes. Guards, retries, and fallbacks belong only where the contract calls for them.
- For substantial work, complete thin, verifiable slices. Keep acceptance cases aligned with the requirement as interfaces evolve; do not build speculative infrastructure first.
- Leave a durable regression check for a repaired defect when it can exercise the real failure. If only temporary or manual verification is possible, explain why and what regression protection remains absent.
- For repeated mechanical edits, verify one transformation before automating the rest, then inspect and check the resulting artifacts.
- When delegation is permitted and useful, give each worker a bounded deliverable, constraints, and required evidence. Isolate writers by files or worktrees; inspect their artifacts and verify the integrated result yourself.
- Before a handoff or context reset during unfinished work, preserve only what is needed to resume: the target, decisions, evidence, unresolved questions, and next action. Do not maintain a transcript of every step.

## Make checks trustworthy

- Derive expected results from requirements, independently checked examples, or authoritative fixtures. Do not compute them through the implementation or helpers being tested.
- Assert the behavior consumers rely on, including observable effects and failures. Name a plausible incorrect implementation the check would reject; internal restructuring that preserves the contract should not break it.
- Keep the subject real. Substitute collaborators only at boundaries outside the claim, preserving their relevant return shapes and failure behavior. Do not mock away the integration being verified.
- When an effect or its absence is the contract, observe it. For example, a rejected request must leave protected state unchanged; an error response alone does not establish that.
- Control clocks and mutable state, synchronize explicitly, and bound asynchronous waits. Clean up owned processes and resources. Do not add production interfaces merely to inspect internals in tests.
- If a check fails, distinguish a product defect, an incorrect expectation, and an environment failure. Do not weaken an accurate check for a green result. Call a failure pre-existing only with baseline evidence; preserve user work while obtaining it.

## Increase scrutiny where consequences require it

| Changed behavior | Additional evidence to seek |
| --- | --- |
| Authorization or security boundary | Allowed and denied cases, including forbidden effects that must not occur |
| Persistence or migration | Existing data, partial failure, and a recovery or deliberate rejection path |
| Public contract | Representative producers and consumers, including errors and compatibility expectations |
| Shared state or retries | Conflicting operations, duplicate delivery, and preserved invariants |

Use property, mutation, fuzz, fault-injection, or independent review when it closes a concrete evidence gap. Diff size and reviewer agreement are not risk measures.

## Inspect the final artifact

- Verify the intended revision and environment. Exercise the original failure or acceptance path and inspect outputs and side effects. A successful run against a stale build does not cover the change.
- Read the final diff for accidental defaults, missing callers, unrelated edits, and temporary instrumentation. Update affected usage documentation; verify changed commands, examples, links, and anchors, marking examples that were not run.
- For an authorized commit, inspect the staged scope and exclude unrelated user changes. After hooks run, inspect the actual commit and working tree; rerun checks if the artifact they covered changed.
- In a review, report location, impact, and evidence for each finding. Separate reproduced defects from reasoned risks and preferences. Do not manufacture findings to fill a quota.
