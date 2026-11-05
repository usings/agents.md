# Agent Guide

This file and every `.agents/0x-*.md` guide are generic and are copied verbatim between repositories. The `.agents/1x-*.md` files describe this project.

- Precedence: the user's explicit instruction, then the project files (`1x`), then the guide that governs the task, then this file. Only the user's explicit instruction overrides a MUST or MUST NOT.
- The project files are a map of the code. Where one disagrees with the source or tests, the code wins; fix the file in the same change.
- **MUST**, **MUST NOT**, **SHOULD** and **MAY** have their RFC 2119 meanings and mark real invariants. Other rules are the default way to work; if you deviate from one, say so and why in the report.

## Start

1. Read [10](.agents/10-project.md) before working in the repository.
2. State the goal in one sentence and the smallest change that meets it. If the evidence rules out the requested change, show the evidence and stop.
3. Before work that a guide governs, read that guide ([Find the guide](#find-the-guide)).

## Autonomy

- Do reversible work without asking: reading, editing files, running local checks. Report the decisions afterward.
- You MUST NOT commit, push, release, rewrite history, delete uncommitted work or data outside version control, or publish or send content to an external service (a pull request, issue, message, or upload) unless the user authorized that action in this task.
- Ask only about product or preference decisions that no experiment or inspection can settle. Investigate everything else.
- For an audit, a review, or a question, report findings. Edit only when asked to fix.
- Give your real judgment. Say so when the evidence contradicts the request or a proposal does not earn its place.

## Make it work

- Name the data shape before writing logic. Choose a structure in which invalid states cannot be written.
- Reproduce first. Write the check that fails and confirm it fails for the expected reason before changing code. If an honest check is impractical, say why instead of writing a weak one.
- Make the smallest change that solves the problem. One decision lives in one place.
- Fix the first wrong decision, not the place the failure surfaced. A guard, retry, or swallowed error that hides a state that should never exist is not a fix.
- When two fixes that share one premise have failed the same check, write the premise in one sentence and test it before trying a third.
- When a new requirement does not fit the current design, design as if it had been there from the start, then deliver it in steps that each end in a passing check.

## Make it right

- Remove before adding: dead code, one-caller wrappers, unused options. Add abstraction, configuration, or compatibility paths only for a present need.
- When replacing an internal API, migrate every caller and delete the old one in the same change, unless a project file declares it a compatibility contract.
- Leave unrelated code alone. Mention problems you noticed in the report.
- When the same correction is needed twice, enforce it with structure instead of another sentence ([04](.agents/04-instructions.md#encode-lessons)).

## Verify

- You MUST verify a result before claiming it. Check the real artifact: run the behavior and read the actual output. Compiling, a self-report, or an unrelated passing test is not evidence.
- Before handoff, the gates in [10](.agents/10-project.md#commands) MUST pass. A gate that fails without your change too is pre-existing: do not fix it, show the failure, and say which claims it prevents you from verifying.
- Rerun the affected checks after the last edit. An earlier result counts only if nothing it depends on has changed.

## Report

Lead with the goal, then: what changed, the evidence (command and result), compatibility effects, and open risks or decisions. Mark each check passed, failed, not run, or blocked. Mark each claim verified or inferred.

## Find the guide

| Task | Read |
| --- | --- |
| Writing, changing, or judging tests | [01](.agents/01-testing.md) |
| Designing or refactoring an interface, module boundary, data model, or state | [02](.agents/02-design.md) |
| Writing or editing documentation for readers | [03](.agents/03-docs.md) |
| Editing `AGENTS.md`, `.agents/`, prompts, or skills; a correction needed twice | [04](.agents/04-instructions.md) |
| Delegating to subagents or running work in parallel | [05](.agents/05-delegation.md) |
| Committing or writing a commit message | [06](.agents/06-commits.md) |
| Tidying up or redesigning existing code; assessing architecture | [07](.agents/07-tidyup.md) |
| Stack, layout, commands, contracts, project rules; `10` links to any other `1x` file | [10](.agents/10-project.md) |
