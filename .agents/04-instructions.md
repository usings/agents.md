# 04 — Agent Instructions

Read before editing `AGENTS.md`, `.agents/`, prompts, or skills, and when the same correction is needed twice.

## Layout

- `AGENTS.md` is loaded automatically. It holds the rules every task needs and the table that routes to guides. Keep it at most 80 lines.
- `AGENTS.md` and the `0x` guides MUST NOT contain anything specific to one project, such as its paths, commands, or domain terms. Widely shared conventions, such as a commitlint preset, are not project-specific.
- `1x` files describe the project. Start with `10-project.md`. When it grows past 80 lines, or a topic in it becomes independent of the rest, move that topic into `11-…`, `12-…`, and link every other `1x` file from `10-project.md`.
- Give each guide one topic that few tasks share with another guide. A rule nearly every task needs belongs in `AGENTS.md`, not in a guide.
- Open each guide with one sentence saying when to read it. When you add, rename, or remove a guide, update the table in `AGENTS.md`.

## Writing rules

- Keep only sentences that change a decision. Write imperatives; give a reason only where the rule is confusing without one.
- Make each rule checkable: name the observable condition, or the test that shows it was followed.
- Use MUST only for real invariants. Do not add escape clauses such as "where practical" or "as needed"; if a rule has a real exception, name it.
- State each rule once, in the file that owns it, and link to it from elsewhere.

## Encode lessons

When the same mistake happens twice, fix it at the highest level that works:

1. Architecture: one owner per piece of state, one supported way per task, unreachable internals.
2. Types, so the wrong code does not compile.
3. A lint or check whose error names what to use instead.
4. A behavior test.
5. Prose, only for a judgment call that nothing can check.

Prove that a new check fails on the real past mistake. Record the rule and what enforces it in the rules table of [10-project](10-project.md#rules). Delete a rule once its mistake can no longer happen.

## Verifying an instruction change

- Check statically: links and anchors resolve, every guide is reachable from the table in `AGENTS.md`, no two rules conflict, precedence is unambiguous, and `AGENTS.md` and the `0x` files contain nothing project-specific.
- When a change alters consequential behavior, run a realistic task in a fresh session with the same tools and permissions. Write the pass criteria first and judge the actions against them. To claim a change fixed a behavior, first reproduce the failure without it.
- If no trial ran, report the findings as static and do not claim improved behavior.
