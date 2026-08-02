# Requirements — <project>

<!-- The only file a human edits during a round. Fill the three boxes in "Given" below,
     then say: "Read docs/REQUIREMENTS.md and draft the rest." Everything under
     "Drafted" is written by the agent and confirmed by me — reviewing a draft is faster
     than filling a form, and the draft itself is the requirements-clarifying step.

     Anything not written in this file is not being built. -->

## Given

<!-- Human-filled. Nothing else in this file is. -->

### Problem as given

<!-- Verbatim, unparaphrased. The Goal and criteria below are checked back against this. -->

### Their rules

<!-- Conventions supplied by the interviewer — stack, structure, libraries, testing, style.
     These win over the Conventions section of CLAUDE.md wherever the two disagree.
     Empty means CLAUDE.md is the standard. -->

### Round

- Length:
- Started:
- Stop building at: <!-- length minus 10 min: green the check, commit, write DECISIONS. -->

---

## Drafted

<!-- Agent-written from "Given", confirmed by me before any code is written.
     Draft it all at once and ask about what's genuinely ambiguous — don't
     interview me section by section. -->

### Goal

<!-- One sentence. What can a user do at the end that they can't now? -->

### Acceptance criteria

<!-- Numbered, observable, demoable. "Fast" and "clean" are not criteria; "results filter
     within 300ms of typing" is. Ordered by priority — built top-down, so what falls off
     the bottom is what was chosen to drop. -->

1.
2.
3.

### Edge cases

<!-- Empty state, one item, huge list, duplicate input, superseded in-flight request,
     network failure, whitespace/casing. List them even where the decision is "ignore for
     now" — deferred deliberately is a decision; unnoticed is a gap. -->

-

### Cut list — explicitly NOT building

<!-- Deferred ideas land here instead of in the code. Usual suspects if they apply:
     persistence, auth, responsive layout, retry UI, accessibility beyond semantic HTML. -->

-

### Data

<!-- Endpoint(s), or the shape of local fixture data. One real sample payload is worth
     more than a prose description of the schema. -->

```json

```

### Assumptions

<!-- Stated, not asked. Each one is something I can be challenged on, so keep them few. -->

-

### Open questions

<!-- Genuinely blocking — for the interviewer, not for me. Ask them early. -->

-

## Done means

- [ ] `npm run check` green (typecheck, lint, tests)
- [ ] Every acceptance criterion above demoable in the browser
- [ ] `docs/DECISIONS.md` current — every real choice has its rejected alternative
