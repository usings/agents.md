# 06 — Commits

Read before committing or writing a commit message. Committing needs authorization ([Autonomy](../AGENTS.md#autonomy)).

## Scope

- Inspect the diff and the staged scope first, and leave the user's unrelated changes out.
- Split commits by intent that can be explained and verified on its own.
- Hooks can rewrite staged content, so inspect the resulting commit and the working tree afterward.

## Message

- Header: `type(scope)!: subject`, at most 100 characters; `(scope)` and `!` are optional.
- `type` is lower case and one of `build`, `chore`, `ci`, `docs`, `feat`, `fix`, `perf`, `refactor`, `revert`, `style`, `test`.
- `subject` is not empty, does not start with a capital letter, and does not end with a period.
- A blank line separates the header, body, and footers; body and footer lines are at most 100 characters. The body says why.
- Mark a breaking change with `!` before the colon or a `BREAKING CHANGE:` footer.
