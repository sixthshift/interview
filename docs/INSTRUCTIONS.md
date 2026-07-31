# Project structure & formatting expectations

<!-- My version of the doc an interviewer might hand over. Two uses:
     1. They give you theirs → paste theirs into CLAUDE.md; that wins, ignore this.
     2. They don't → this stands as-is, so structure is settled before the agent
        invents its own. CLAUDE.md already points here. -->

## Structure

`src/` starts as hello world. Create these as the task needs them — not up front:

```
src/
  App.tsx            composition + layout only
  components/        presentational, one component per file, named export
  hooks/             use* hooks
  lib/               framework-free logic: transforms, parsing, network seams
  index.css          the only stylesheet (Tailwind entry)
docs/
  REQUIREMENTS.md    scope, acceptance criteria, cut list
```

Rules:

- A file's name says what it is, never what layer it lives in. No `*Service`, `*Manager`, `*Utils`.
- One concern per file. If a file needs section-banner comments, it's two files.
- Types live beside the code that owns them; props types sit directly above the component.
- New file has a determined home before it's written. If there's no home, that's a design question, not a `misc/`.

## Formatting

No formatter is installed — match the existing style rather than reformatting anything:
no semicolons, single quotes, two-space indent, ~100 columns.

If their instructions doc demands an enforced formatter, `npx prettier --write .` runs
without adding a dependency.

- Tailwind utilities for styling. No inline `style` props, no new CSS files.

## Code

- `const` bindings; no reassignment. No class components.
- Guard clauses first, happy path last and unindented.
- Comments carry _why_ — rationale, constraint, surprise. Never restate the code.
- Validate untrusted input at the boundary, then trust it inward. Don't re-check downstream.
- Errors throw typed objects carrying their own disposition. No `Result`/`Either` threading.

## Verification

`npm run check` — typecheck, lint, tests. Green before "done" is said, every time.
A failing check is information to report, never something to silence by weakening the check.

## Commits

Conventional, imperative subject, scoped small enough to describe in one line.
