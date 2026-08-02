# Interview starter

A prepared workspace for timed, AI-assisted coding rounds: a running app, a green test
gate, and the conventions written down, so the round is spent on the problem rather than
on scaffolding.

Vite 8 · React 19 · TypeScript 6 · Tailwind 4 · vitest 4 + React Testing Library.

```sh
npm ci
npm run dev
```

`npm ci` installs the committed lockfile exactly, rather than resolving anything new.

## Scripts

| Script              | Does                                        |
| ------------------- | ------------------------------------------- |
| `npm run dev`       | Dev server on 5173                          |
| `npm run check`     | `tsc -b` → `oxlint` → `vitest run`          |
| `npm test`          | vitest in watch mode                        |
| `npm run build`     | Typecheck, then production build to `dist/` |
| `npm run preview`   | Serve the built output                      |
| `npm run typecheck` | `tsc -b` alone                              |
| `npm run lint`      | oxlint alone                                |

`npm run check` is the gate: it must be green before any change is called done.

## Layout

```
src/
  App.tsx            hello world — replace it
  App.test.tsx       one passing test
  index.css          the only stylesheet (Tailwind entry)
  main.tsx           root render
  vitest.setup.ts    jest-dom matchers
docs/
  REQUIREMENTS.md    the brief — the only file edited by hand during a round
  DECISIONS.md       agent-appended log of choices and their rejected alternatives
CLAUDE.md            agent brief: what's graded, the round's phases, conventions
```

There are no `components/`, `hooks/`, or `lib/` directories yet — `CLAUDE.md` documents
where each belongs, and they get created when something needs them.

A round is worked on its own branch, so resetting for the next one is `git switch main`
rather than emptying the two `docs/` files by hand.

## Notes

- No prettier and no ESLint. oxlint covers `rules-of-hooks`; formatting is by hand
  (no semicolons, single quotes, ~100 columns), or `npx prettier --write .` ad hoc.
- `noUnusedLocals` and `noUnusedParameters` are off, so work-in-progress doesn't fail
  the typecheck.
- vitest must stay on 4.x — vitest 3 bundles its own Vite and collides with Vite 8.
- Requires npm ≥ 11.19. Older npm (11.5.2) fails on this tree with
  `Cannot read properties of null (reading 'edgesOut')`.
