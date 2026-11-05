# 03 — Documentation

Read before writing or editing documentation for readers. Where the docs live is in the [layout](10-project.md#layout) of 10-project.

- Organize around the reader's task. Put prerequisites before the steps that need them. Split pages by independent tasks, not by length or module boundaries.
- Ground every command, flag, default, output, and compatibility claim in current project evidence. Never document a capability that does not exist. Mark examples you did not run.
- Describe the current design. After a behavior change, rewrite the affected explanation instead of appending exceptions about the old one.
- Give each shared detail one canonical home and link to it.
- Explain placeholders, expected success, meaningful failures, limits, and cleanup where the reader needs them.
- Cut filler, marketing words, repeated summaries, and decorative formatting. Keep technical distinctions, warnings, and caveats.
- Follow the target renderer and the existing terminology. Use semantic Markdown and accurate code-fence languages. Give diagrams a text alternative.
- Preserve working links and incoming anchors. Edit the source of generated docs, not the output.
- Verify the affected snippets, links, and anchors with the existing project checks. Report what you checked only by reading.
