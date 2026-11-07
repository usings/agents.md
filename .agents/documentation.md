# Documentation

Read when writing, reviewing, or maintaining documentation for people or agents. Choose useful content, organize it for the reader, write clearly, ground claims in evidence, and keep the document accurate as the system changes.

## Choose what to document

- Identify the reader, their starting knowledge, and the result the document should enable. Choose a primary purpose: guided learning, completing a task, looking up facts, or understanding a concept. Include limits and failure cases that affect that purpose.
- Explain a system through a representative path: what starts it, where data goes, which decisions matter, and what the reader observes. Link relevant entry points instead of narrating every file or function.
- For agent-facing material, prioritize decisions and context that are costly to recover: conventions, constraints, rationale, and non-obvious pitfalls. Link readily discoverable inventories rather than reproducing them.

## Organize for the reader

- Lead with the result or question answered. Put prerequisites and warnings before the actions they govern; give procedures observable completion conditions. Keep lookup detail and background out of the main sequence when links can serve them.
- Keep a concept's definition, rules, and exceptions together. Split by distinct reader tasks or conditional branches, not arbitrary length. A link to optional material should state what it covers and when to read it.
- Use descriptive headings, ordered steps for sequences, and tables for comparable facts. Add examples or diagrams when they resolve an ambiguity; keep the explanation understandable without relying on decoration.

## Write clearly

- Use the project's domain terms and exact public names for commands, flags, symbols, and UI controls. Define unfamiliar terms on first use. When a term has different meanings across contexts, name the context; resolve conflicting meanings with concrete examples before standardizing them.
- Name the actor and action. Put conditions near the claims they limit and before instructions they control. Use ordinary words, explicit referents, and complete sentences; preserve qualifications needed for correctness rather than compressing them away.
- Replace promotional claims, vague attribution, repeated summaries, and ornamental jargon with specific behavior or evidence. Delete text that adds no useful information, without imposing fixed sentence lengths or punctuation bans.

## Establish what is true

- Check commands, defaults, errors, limits, and compatibility against the relevant implementation, runtime, specification, or official documentation. Use sources for the documented version; link non-obvious factual claims to the source that supports them.
- Separate how the system works from why it was designed that way. Trace rationale to decisions, history, or stated requirements; label inferred motives and unresolved contradictions. A plausible explanation is not evidence of historical intent.
- Exercise changed examples under their stated prerequisites and inspect outputs and side effects. Mark examples that were not run and the limits of source-only checks. Validate affected links, anchors, and rendered structure with the project's available tools.

## Keep it accurate

- Give shared facts one authoritative home and link to it. Generate repetitive reference from schemas or code when an existing mechanism supports it; edit the source of generated documentation.
- Update affected documentation with behavior or interface changes. Search for obsolete names and duplicated instructions, revise the canonical explanation, and update incoming links when moving material. Keep old behavior only where a supported version or migration needs it, clearly scoped.
- Reuse the project's glossary for resolved domain meanings, keeping implementation choices out of definitions. Record a design decision when a costly-to-reverse trade-off would otherwise be surprising. Create these records only when there is content to preserve, and mark superseded decisions as historical rather than leaving them as current guidance.
