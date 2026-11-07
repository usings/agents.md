# Agent Instructions

Read when changing agent instructions or evaluating their effectiveness. Keep these guides reusable across repositories; project facts and scoped rules belong in [project context](project.md). Use [Documentation](documentation.md) for content, organization, clarity, evidence, and maintenance.

## Maintain the contract

- Keep only rules that change a decision. State the triggering condition and expected action; distinguish requirements from engineering defaults.
- Give each rule one owner. Put common execution boundaries in [AGENTS.md](../AGENTS.md), conditional methods in topic guides, and destination-specific commands and contracts in project context. Split by task or decision, not line count.
- When an error recurs, identify the mechanism and evidence before editing instructions. Prefer structural enforcement; add prose for judgment that types, tests, or tools cannot enforce. Update or remove the existing rule instead of appending an exception.
- When replacing an installation, preserve customized facts and local rules before deleting superseded files. Update incoming links and the root routing together; do not retain duplicate instruction trees or erase unrelated files.
- Do not introduce required tools or workflows without evidence that the destination provides them. Keep platform-specific permissions and tool configuration out of generic engineering guidance.

## Verify changes

- Inspect local links and anchors, guide reachability from the root, rule ownership, and conflicts. Use the destination's existing checks when available; a prose-only package does not need a new toolchain for this.
- For consequential rule changes, define acceptance conditions and compare representative tasks in fresh sessions. Compare actual outcomes, unsupported claims, unauthorized actions, and cost rather than compliance counts.
- Without fresh-session trials, report static findings only. Do not claim that clearer wording has established better agent behavior.
