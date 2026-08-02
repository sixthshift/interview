# Decisions

<!-- Agent-maintained, append-only, newest last. This is what I read from in the discussion
     phase, so it has to survive the chat transcript scrolling away.

     Append a line the moment a choice is made — not in a batch at the end. A choice is
     worth a line when a competent engineer could have gone the other way: a library, a
     data shape, a boundary, an edge case knowingly left unhandled, a shortcut taken for
     time. Mechanical steps are not decisions.

     Format — one line each, the loser is not optional:

       - **<choice>** over <rejected alternative> — <why the alternative loses>.

     Example:

       - **Debounce in the hook** over debouncing in the input component — the component
         would own timing it can't see the request lifecycle for.
       - **Ignore superseded in-flight responses** over aborting them — 40 lines of
         AbortController for a race the fixture can't produce; noted in the cut list.

     Deliberate omissions get a line too, marked so I can raise them before I'm asked:

       - **Known limit:** no empty-state copy — criterion 4 was cut for time. -->

-
