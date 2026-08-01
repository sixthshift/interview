# Project Instructions

Timed build. Optimise for a working, demoable increment over completeness.

## Their rules

<!-- PASTE any supplied instructions doc here, verbatim, before writing any code.
     A supplied doc wins over anything in docs/INSTRUCTIONS.md. -->

_(nothing pasted yet — until something is here, `docs/INSTRUCTIONS.md` is the standard.
Follow it rather than inventing conventions.)_

## Scope

`docs/REQUIREMENTS.md` is the brief. Read it before proposing or writing anything, and
build criteria in the order listed. Don't build past it — out-of-scope ideas go in its
Cut List, not the code.

Don't add a dependency without asking; each one is a decision that has to be justified.

## The gate

`npm run check` = typecheck → lint → tests. Run it before claiming any task is done.
Never report done on unverified code, and never weaken a test to make it pass.

## Surface your decisions

I have to explain and defend every line of this code, so silent choices cost me.

- Name the trade-off when you pick between real alternatives, in one line, as you make it.
- Say when you're unsure or guessing rather than committing quietly.
- Flag anything you notice that isn't in `docs/REQUIREMENTS.md` — an edge case, a race, a
  wrong-looking assumption — instead of fixing it silently or ignoring it.
- Keep diffs small enough to read in one pass. I review everything.

## Conventions

See `docs/INSTRUCTIONS.md` — structure, formatting, and code rules live there.

`src/` is deliberately near-empty: `App.tsx` is hello world, and there are no
`components/`, `hooks/`, or `lib/` directories yet. Create them when the task needs
them, per the structure section of `docs/INSTRUCTIONS.md`.
