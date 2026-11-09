# agents.md

A reusable instruction package for coding agents. It sets execution boundaries (what an agent may do without asking), how it should investigate and change a repository, and how it should report evidence. The guides are written to be copied into another repository and adapted there.

[AGENTS.md](AGENTS.md) is the entry point. It holds the rules that apply to every task and routes to topic guides that agents read only when a task needs them.

## Contents

| Path | Purpose |
| --- | --- |
| [AGENTS.md](AGENTS.md) | Authority and scope, decision rules, evidence and completion requirements, and routing to the topic guides |
| [.agents/project.md](.agents/project.md) | Template for the destination repository's purpose, commands, contracts, and local rules |
| [.agents/engineering.md](.agents/engineering.md) | Investigating behavior, implementing and reviewing changes, evaluating tests, committing |
| [.agents/design.md](.agents/design.md) | Interfaces, ownership, state models, and architecture |
| [.agents/documentation.md](.agents/documentation.md) | Writing and maintaining documentation for people or agents |
| [.agents/instructions.md](.agents/instructions.md) | Changing agent instructions and evaluating their effect |
| [.agents/evals/scenarios.md](.agents/evals/scenarios.md) | Maintainer-only evaluation cases; not read by agents at runtime |

## Adopt in a repository

1. Copy `AGENTS.md` and the `.agents/` directory into the destination repository's root. Do not copy this README. `.agents/evals/` is needed only if you will evaluate changes to the guides.
2. If the destination already has agent instructions, merge rather than overwrite: keep its project facts and local rules, and give each rule one home as described in [.agents/instructions.md](.agents/instructions.md).
3. Fill in [.agents/project.md](.agents/project.md) with verified facts: entry points, required checks and their commands, external contracts, and local rules. Leave sections marked as not recorded until you have verified them; agents are instructed to inspect the repository instead of assuming that missing entries mean nothing exists.
4. If your agent tool does not read `AGENTS.md` on its own, point its instruction file at it. For example, a Claude Code `CLAUDE.md` can contain the line `@AGENTS.md` to import it.

Keep the topic guides generic. Repository-specific commands, contracts, and rules belong in `.agents/project.md`, which keeps later updates to the shared guides from overwriting local customizations.

## Change the guides

Follow [.agents/instructions.md](.agents/instructions.md) when editing any guide: keep only rules that change a decision, put each rule in one place, and update routing in `AGENTS.md` together with any renamed or added guide.

A static review can find broken links, duplicated rules, and conflicts, but it cannot show that agents behave better. For consequential changes, compare the baseline and candidate in fresh sessions using [.agents/evals/scenarios.md](.agents/evals/scenarios.md). That file contains acceptance specifications only; no evaluation results are recorded in this repository.
