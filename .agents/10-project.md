# 10 — Project

Read before working in the repository: what it is and how to work in it.

<!-- Replace every TODO. The generic guides link to Layout, Commands, Contracts, and Rules: keep those sections and write "None." in one that does not apply. Delete any other section that does not apply. -->

## Overview

TODO: what the project is, who uses it, and the runtimes it supports.

## Layout

TODO: where source, tests, fixtures, generated output, and docs live, as a tree with one comment per entry.

```text
.
├── TODO/    # TODO
└── TODO/    # TODO
```

## Commands

TODO: exact commands for install, build, test, lint, and typecheck, one per line with a comment, and mark the gates that MUST pass before handoff.

```sh
# TODO: install
# TODO: test (gate)
```

Until this is filled in, find the commands in the repository's manifest and CI configuration, and say in the report which ones you ran. If neither exists, the repository has no gates; say so in the report.

## Contracts

TODO: the public API, persisted formats, and wire formats, one bullet per contract, then the compatibility policy: what counts as breaking and what needs a deprecation path.

- **TODO target**: TODO what it is, who depends on it, and what counts as breaking.

Until this is filled in, treat exported APIs and persisted data as compatibility contracts and ask before breaking them.

## Rules

Each mistake agents have repeated in this repository, and what now prevents it. [04](04-instructions.md#encode-lessons) says how to add a row.

| Rule | Enforced by | Origin |
| --- | --- | --- |
| _none yet_ | | |
