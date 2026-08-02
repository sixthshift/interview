# Project Instructions

A timed, AI-assisted interview round. I am being assessed — you are the tool I am assessed
on using. A working, demoable increment beats completeness, every time.

## What's being graded

Three dimensions, and only one of them is the code:

- **Engineering problem-solving** — did the ambiguity get explored before the typing started.
- **Technical depth & ownership** — can I explain and defend every line, including yours.
- **AI collaboration effectiveness** — did I direct you, or narrate whatever you produced.

The named failure modes, all three of which are things you can cause:

- **AI showcase** — output volume as the point. It isn't.
- **Feature marathon** — six half-built criteria instead of two finished ones.
- **Hands-off** — code lands that I can't account for.

So: **never hand me code I haven't been given the chance to understand.** Small diffs,
reviewable in one pass, one concern at a time. If a change is too big to read in a sitting,
it was too big to write.

## The round

**Plan.** `docs/REQUIREMENTS.md` is the brief and the only file I edit. I fill the "Given"
section; you draft the rest and I confirm it before any code is written. Draft it in one
pass, then ask about what is genuinely ambiguous — questions for the interviewer go under
Open questions, not to me. Nothing gets built until the criteria are agreed.

**Build.** Criteria in the listed order, top-down. Finish one before starting the next.
Don't build past the brief — out-of-scope ideas go in its Cut List, not the code.
Don't add a dependency without asking; each one is a decision I have to justify.

**Discuss.** At the "stop building" time in the brief: stop, green the gate, commit, and
bring `docs/DECISIONS.md` current. Say what's unfinished plainly — a known limit I raise
first is worth more than one the interviewer finds.

## Surface your decisions

I have to defend every line, so silent choices cost me.

- Name the trade-off when you pick between real alternatives, in one line, as you make it.
- Append it to `docs/DECISIONS.md` then, not in a batch at the end. The chat scrolls away;
  that file is what I read from in the discussion.
- Say when you're unsure or guessing rather than committing quietly.
- Flag anything you notice that isn't in the brief — an edge case, a race, a wrong-looking
  assumption — instead of fixing it silently or ignoring it.

## The gate

`npm run check` = typecheck → lint → tests. Green before any task is called done.
Never report done on unverified code, and never weaken a test to make it pass — a failing
check is information to report, not something to silence.

## Commits

Commit each time the gate goes green, without asking. This overrides my usual
stop-at-staging rule: the commit history is the build story I walk through at the end, and
a rollback point matters more here than a review queue. Conventional, imperative subject,
one line.

## Conventions

Interviewer-supplied rules go in the brief under "Their rules" and win over everything
below. Where that section is empty, this is the standard — follow it rather than inventing
conventions.

### Structure

`src/` starts as hello world — no `components/`, `hooks/`, or `lib/` yet. Create them when
a task needs them, not up front:

```
src/
  App.tsx            composition + layout only
  components/        presentational, one component per file, named export
  hooks/             use* hooks
  lib/               framework-free logic: transforms, parsing, network seams
  index.css          the only stylesheet (Tailwind entry)
```

- A file's name says what it is, never what layer it lives in. No `*Service`, `*Manager`, `*Utils`.
- One concern per file. If a file needs section-banner comments, it's two files.
- Types live beside the code that owns them; props types sit directly above the component.
- A new file has a determined home before it's written. If there's no home, that's a design
  question, not a `misc/`.

### Formatting

No formatter is installed — match the surrounding style rather than reformatting anything:
no semicolons, single quotes, two-space indent, ~100 columns. If their rules demand an
enforced formatter, `npx prettier --write .` runs without adding a dependency.

Tailwind utilities for styling. No inline `style` props, no new CSS files.

### Code

- `const` bindings; no reassignment. No class components.
- Guard clauses first, happy path last and unindented.
- Comments carry _why_ — rationale, constraint, surprise. Never restate the code.
- Validate untrusted input at the boundary, then trust it inward. Don't re-check downstream.
- Errors throw typed objects carrying their own disposition. No `Result`/`Either` threading.
