# 01 — Testing

Read before writing, changing, or judging tests. Test commands are in [10-project](10-project.md#commands), and test and fixture locations in its [layout](10-project.md#layout).

## What a test must do

A test is a claim about what users of the code can observe through the interface they use: return values, errors, state they can read back, and effects on outside systems. Judge every test against two imagined edits:

- **Break the behavior.** Return a wrong value, skip an effect, or do it twice. The test MUST fail. A test that would still pass if every function returned nothing proves nothing.
- **Change the internals.** Keep every observable result and restructure underneath. The test SHOULD keep passing; if it fails, it is pinned to the implementation.

Keep the tests that pass both checks. Rewrite or delete the rest.

## Writing tests

- Test at the smallest layer that exercises the behavior. Add a durable test when it protects a requirement, not for a reversible cosmetic edit.
- Derive the expected value from the requirement, a literal, or a checked-in fixture, never from the code or helpers under test.
- Assert what the contract promises, no less and no more. Pin exact strings or bytes only when the format is the contract. Assert the error type callers branch on, not message wording no caller reads.
- For a regression, write the focused case that failed before the fix. Cover the failure paths and boundaries the change can reach, not a coverage quota.
- When a call or its absence is the contract ("an empty cart never charges"), assert it, and pair it with a case where the call happens so the test shows it can see the call.
- Match the evidence to the claim: a compiler run for type claims, execution in the owning runtime for runtime claims, snapshots only for intentional output contracts.

## Doubles

Keep the component under test real. Place doubles at slow or external boundaries, and make them keep the real return shapes, errors, and side effects. When a mock is harder to maintain than the real collaborator, use the real one.

## Reliability

- Synchronize explicitly and control clocks. Do not sleep for an arbitrary time.
- Every asynchronous check MUST terminate. Clean up processes, servers, timers, open handles, and temporary files.
- Isolate mutable state so tests pass in parallel and in any order.
- Keep test-only setup in test utilities. Do not add production lifecycle methods only for tests.

## Before finishing

Pick one plausible wrong implementation (a wrong branch, a missing effect, a wrong argument) and name the assertion that fails. If none does, close the gap. When a test's sensitivity is in doubt, substitute the wrong result temporarily and watch the test fail.
