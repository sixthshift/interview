# Interview starter

Vite 8 · React 19 · TypeScript 6 · Tailwind 4 · vitest 4 + React Testing Library.
Template repo for a 60-minute AI-assisted build — clone it and start.

```sh
git clone <this-repo> my-app && cd my-app
npm ci          # lockfile install, ~10s
npm run dev
```

`npm ci` not `npm install` — it installs the committed lockfile exactly and refuses to
silently resolve something new, which is what you want when the clock is running.

## First five minutes

1. **Paste their instructions doc** into `CLAUDE.md` under `## Their rules`. Theirs
   overrides `docs/INSTRUCTIONS.md` — paste, don't merge. If they didn't give you one,
   `docs/INSTRUCTIONS.md` already stands and `CLAUDE.md` already points at it.
2. **Paste the problem verbatim** into `docs/REQUIREMENTS.md` under "Problem as given",
   then restate it below as numbered criteria, edge cases, and a cut list. Do this with
   them watching — the breakdown is the assessed work, not overhead before it.
3. Build. Prompt at the file, not at the chat:
   `"Read docs/REQUIREMENTS.md. Implement criterion 2 only, then run npm run check."`

## The three files

|                        | Written                 | During the session                     |
| ---------------------- | ----------------------- | -------------------------------------- |
| `CLAUDE.md`            | Before the call         | One paste at minute 1, then untouched  |
| `docs/REQUIREMENTS.md` | Live, from minute 5     | Constantly — it's the working document |
| `docs/INSTRUCTIONS.md` | Before the call, frozen | Never edited; reference only           |

`CLAUDE.md` is loaded every turn, so length is a real cost — keep it standing orders only.
`docs/REQUIREMENTS.md` is where the problem, the criteria, the cuts, and the running
notes live, because chat context gets compacted and a file gets re-read fresh every turn.
If you'd otherwise say something to the agent twice, it belongs in a file.

## Layout

```
src/
  App.tsx                hello world — replace it
  App.test.tsx           one passing test, so the harness is proven not just installed
  index.css              the only stylesheet — Tailwind entry
  main.tsx               root render
  vitest.setup.ts        jest-dom matchers
docs/
  REQUIREMENTS.md        scope, acceptance criteria, cut list — fill this
  INSTRUCTIONS.md        structure + formatting rules, if they don't supply theirs
CLAUDE.md                agent brief; points at docs/
.claude/settings.json    pre-allowlists this project's commands
```

Five files in `src/`, nothing else. No `components/`, `hooks/`, or `lib/` — their homes
are documented in `docs/INSTRUCTIONS.md` and get created when the task earns them. There
is deliberately no example code to read, imitate, or delete.

## The gate

`npm run check` = `tsc -b` → `oxlint` → `vitest run`. Make the agent run it before it
says done. Four seconds, and it turns "I think it works" into evidence — the single
highest-leverage habit in the session.

## The 60 minutes

| Time      | Doing                                                                     |
| --------- | ------------------------------------------------------------------------- |
| 0:00–0:05 | Clone, `npm ci`, `npm run dev`. Read their docs. Ask blockers now.         |
| 0:05–0:12 | Paste the problem into `docs/REQUIREMENTS.md`, restate it as criteria.     |
| 0:12–0:20 | Thinnest end-to-end slice: real data on screen, ugly. Commit.              |
| 0:20–0:45 | Criteria in priority order, one at a time. `npm run check` + commit each.  |
| 0:45–0:52 | Tests on the logic that would embarrass you if wrong. Polish the visible.  |
| 0:52–1:00 | Stop building. `npm run check`. Walk the demo, trade-offs, and next steps. |

Leave time at the end deliberately. Three criteria working and explained beats five
half-built, and the wrap-up is where the trade-offs you made become visible as decisions
rather than as things you ran out of time for.

Two habits that matter more than the schedule: **say what you'd do before you ask the
agent** — your own answer first, then use it to check the agent's — and **read every diff**.
Both are stated expectations, not just good manners.

## Deliberate choices

- **npm** — matches whatever starter an interviewer hands over, and whoever runs it after.
- **Tailwind, not CSS modules** — a visual change stays inside one `.tsx`, so the agent
  makes one edit instead of coordinating two files, and there are no class names to review.
- **No ESLint** — oxlint ships with Vite, runs in 0.2s, and its `rules-of-hooks` check
  catches a runtime crash class `tsc` can't see. That's the whole reason it's kept.
- **No prettier, no AGENTS.md** — nothing formats on save; match the surrounding style, or
  `npx prettier --write .` ad hoc. `CLAUDE.md` is the only agent brief, so a non-Claude
  agent needs pointing at it manually.
- **`noUnusedLocals` off** — half-written code must not red-light your own gate mid-build.
- **No devcontainer** — image build, macOS bind-mount HMR flakiness, and port forwarding
  are three new failure modes at minute zero, buying isolation a throwaway doesn't need.
  `.claude/settings.json` is the part that actually saves turns.
- **vitest 4** — vitest 3 bundles its own Vite and its plugin types collide with Vite 8.
  Keep this pinning in mind on any dependency refresh.

## Known limits

- Verified on one machine, from a clean `npm ci`: `check` green, `build` green with Tailwind
  compiled into `dist`, dev server serving on 5173, and HMR confirmed over the Vite
  websocket (`js-update` for `src/App.tsx`). Never driven through a real timed run; the
  table above is reasoning, not measurement.
- `node_modules` is gitignored, so a clone installs from the lockfile. **npm 11.5.2 fails
  on this tree** with `Cannot read properties of null (reading 'edgesOut')` — an arborist
  bug; 11.19.0 is fine. Run `npm i -g npm@latest` before you need it.
- npm ≥11.19 blocks install scripts by default and will warn about `fsevents`. Harmless
  here — fsevents ships a prebuilt binary, and HMR was verified with the script ungranted.
  No need to `npm install-scripts approve` anything mid-interview.
- Pinned versions age. After any refresh, re-run `npm run check` and `npm run build`.
