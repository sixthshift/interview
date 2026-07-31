# Requirements — <project>

<!-- The working document for the session. Paste the problem in, restate it as criteria,
     then keep editing it as scope moves. Anything not written here is not being built.

     Prompt the agent AT this file rather than re-describing the task:
       "Read docs/REQUIREMENTS.md. Implement criterion 2 only, then run npm run check." -->

## Problem as given

<!-- Their words, verbatim, pasted before anything else. Never paraphrased — when the
     restatement below drifts, this is what you check it against. -->

## Goal

<!-- One sentence, mine not theirs. What can a user do at the end that they can't now? -->

## Acceptance criteria

<!-- Numbered, observable, demoable. Each must be something you can point at on screen.
     "Fast" and "clean" are not criteria. "Results filter within 300ms of typing" is.
     Ordered by priority — the agent builds them top-down, and what falls off the bottom
     when time runs out should be what you'd have chosen to drop anyway. -->

1.
2.
3.

## Edge cases

<!-- Empty state, one item, huge list, duplicate input, in-flight request superseded,
     network failure, whitespace/casing. Name them even where the decision is "ignore for
     now" — a named-and-deferred edge is judgement; an unnoticed one is a gap. -->

-

## Cut list — explicitly NOT building

<!-- Every idea that comes up and gets deferred lands here instead of in the code. Say these
     out loud as you cut them — naming a trade-off is the work; silently running out of time
     is not.

     Usual suspects, if they apply: persistence, auth, responsive layout, retry UI,
     accessibility beyond semantic HTML and labels. Write the ones you actually cut —
     an unedited list reads as boilerplate rather than a decision. -->

-

## Data

<!-- Endpoint(s), or the shape of local fixture data. Paste one real sample payload — it is
     worth more to the agent than a prose description of the schema. -->

```json

```

## Assumptions

<!-- Decisions made without asking, because asking wasn't worth the time. State them in the
     demo. An unstated assumption reads as a mistake; a stated one reads as judgement. -->

-

## Open questions

<!-- Things genuinely blocking. Ask these early — not at minute 50. -->

-

## Notes / next

<!-- One line every time you take a knowing shortcut, or the agent does something you'd have
     done differently. Read from this at the wrap-up instead of reconstructing from memory —
     it turns "I ran out of time" into "here's what I traded away, and why". -->

-

## Done means

- [ ] `npm run check` green (typecheck, lint, tests)
- [ ] Every acceptance criterion above demoable in the browser
- [ ] Cut list and assumptions stated out loud
