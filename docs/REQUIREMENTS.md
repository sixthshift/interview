# Requirements — <project>

<!-- The brief for this build. Anything not written here is not being built.
     Prompt the agent at this file rather than re-describing the task:
       "Read docs/REQUIREMENTS.md. Implement criterion 2 only, then run npm run check." -->

## Problem as given

<!-- The request verbatim, unparaphrased. The restatement below is checked against this. -->

## Goal

<!-- One sentence. What can a user do at the end that they can't now? -->

## Acceptance criteria

<!-- Numbered, observable, demoable. "Fast" and "clean" are not criteria; "results filter
     within 300ms of typing" is. Ordered by priority — built top-down, so what falls off
     the bottom is what was chosen to drop. -->

1.
2.
3.

## Edge cases

<!-- Empty state, one item, huge list, duplicate input, superseded in-flight request,
     network failure, whitespace/casing. List them even where the decision is "ignore for
     now" — deferred deliberately is a decision; unnoticed is a gap. -->

-

## Cut list — explicitly NOT building

<!-- Deferred ideas land here instead of in the code. Usual suspects if they apply:
     persistence, auth, responsive layout, retry UI, accessibility beyond semantic HTML. -->

-

## Data

<!-- Endpoint(s), or the shape of local fixture data. One real sample payload is worth
     more than a prose description of the schema. -->

```json

```

## Assumptions

<!-- Decisions made without asking. -->

-

## Open questions

<!-- Genuinely blocking. Resolve early. -->

-

## Notes / next

<!-- One line per knowing shortcut, or per thing that would be done differently with more
     time. The record of trade-offs made. -->

-

## Done means

- [ ] `npm run check` green (typecheck, lint, tests)
- [ ] Every acceptance criterion above demoable in the browser
