# AGENTS.md

**`hausfold/.github`** — the org's front page. This repo exists to render one
thing: the profile README shown at <https://github.com/hausfold>.

**This file is the one set of instructions, for every agent.** Claude Code,
Codex, OpenCode, Cursor, Copilot — TUI or GUI — all read *this*, directly or
through a one-line pointer. Nothing harness-specific belongs here; when a flow
needs per-client wiring, the wiring lives in that client's own file and the
*content* stays here or in `.agents/`. The map of which tool reads which file is
[`.agents/README.md`](./.agents/README.md).

## Am I in the right repo? (routing)

**This repo owns THE ORG FRONT PAGE** — the profile README. Nothing else. It
ships no code, has no flake, and nothing downstream pins it.

| Want to change… | Repo |
|---|---|
| the org profile README | here ← **you are here** |
| a tool's own README, banner or app icon | that tool's repo (`haus`, `pounce`, `perch`, `trill`, `nebelung`, `holt`) |
| nebelhaus.com — the site, its logos, per-tool OG images, accents | `workshop` (`web/`) |
| anything about how the family is built (`bench`, the routing table) | `workshop` |

> **Whatever agent you are, enforce this.** A request to change what a *tool*
> looks like or does almost never belongs here — this repo only holds the shop
> window. Point at the right repo before editing.

```
profile/README.md            the org profile page — GitHub renders THIS path, not the repo root
```

## The one thing that will bite you

- **`profile/README.md` is the rendered file, not `README.md` at the root.**
  GitHub only picks up the profile page from `profile/README.md` in a repo named
  `.github`. A root `README.md` here renders nowhere.

## Conventions

- The README is a **router, not documentation**: one line per repo, in the
  family's order (house → apps → theme → substrate → bench), pointing at the
  repo. Depth belongs on <https://nebelhaus.com>, and per-tool detail in that
  tool's own README.
- No banner image. It carried an org-name pun (`nebelhaus` → "raised in the
  fog") that stopped fitting once the org became `hausfold`; the README is
  text-only now.
- Voice: lowercase, spare. Match what's there rather than introducing a new
  register.
- Licensed per repo, no identity, no secrets — same as every repo in the
  family.
