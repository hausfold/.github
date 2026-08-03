# AGENTS.md

**`nebelhaus/.github`** — the org's front page. This repo exists to render one
thing: the profile README shown at <https://github.com/nebelhaus>, plus the
image it carries.

**This file is the one set of instructions, for every agent.** Claude Code,
Codex, OpenCode, Cursor, Copilot — TUI or GUI — all read *this*, directly or
through a one-line pointer. Nothing harness-specific belongs here; when a flow
needs per-client wiring, the wiring lives in that client's own file and the
*content* stays here or in `.agents/`. The map of which tool reads which file is
[`.agents/README.md`](./.agents/README.md).

## Am I in the right repo? (routing)

**This repo owns THE ORG FRONT PAGE** — the profile README and the family
showcase image. Nothing else. It ships no code, has no flake, and nothing
downstream pins it.

| Want to change… | Repo |
|---|---|
| the org profile README / the family showcase image | here ← **you are here** |
| a tool's own README, banner or app icon | that tool's repo (`nebelhaus`, `pounce`, `trill`, `perch`, `nebelung`) |
| nebelhaus.com — the site, its logos, per-tool OG images, accents | `workshop` (`web/`) |
| anything about how the family is built (`bench`, the routing table) | `workshop` |

> **Whatever agent you are, enforce this.** A request to change what a *tool*
> looks like or does almost never belongs here — this repo only holds the shop
> window. Point at the right repo before editing.

```
profile/README.md            the org profile page — GitHub renders THIS path, not the repo root
profile/assets/              images the README references
```

## The two things that will bite you

- **`profile/README.md` is the rendered file, not `README.md` at the root.**
  GitHub only picks up the profile page from `profile/README.md` in a repo named
  `.github`. A root `README.md` here renders nowhere.
- **Images are self-hosted through `raw.githubusercontent.com`,** not relative
  links — a relative image path breaks once GitHub renders the README on the org
  page instead of in the repo. So the URL contains the branch and the exact
  filename:
  `https://raw.githubusercontent.com/nebelhaus/.github/main/profile/assets/<file>`.
  **Keep the filename when you replace an image**, or the org page 404s its own
  banner. The current one is `nebelhaus-family-showcase.png` (1520×870) — the
  official name is "family showcase", not "org banner".

## Conventions

- The README is a **router, not documentation**: one line per repo, in the
  family's order (house → palette → messages → shelf → theme → bench), pointing
  at the repo. Depth belongs on <https://nebelhaus.com>, and per-tool detail in
  that tool's own README.
- A rebrand is a **three-repo change** — the tool's own assets, the site's logo
  and accent under `workshop/web/`, and the family showcase tile here. Landing
  only one of the three leaves the family visibly inconsistent, so say which
  parts you did.
- Voice: lowercase, spare, foggy. Match what's there rather than introducing a
  new register.
- MIT, public, no identity, no secrets — same as every repo in the family.
