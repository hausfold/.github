# `.agents/` — the harness-neutral layer

Every coding agent invents its own dotfile. This directory is the answer to
that: **the content lives here (or in `AGENTS.md`), and each client's own
directory holds nothing but wiring** — a pointer, a symlink, or a hook
registration. Switch harness, keep the flows.

> **One body, many pointers.** A rule, a flow, or a script is written *once*. If
> a file under `.claude/`, `.codex/`, `.opencode/` or `.github/` carries a
> project rule rather than a reference to one, it's a bug — the next agent, on a
> different client, runs without it.

Corollary: never "fix" a stale pointer by copying the current text into it.

The family-wide rationale — the four kinds of agent config, how to add a new
harness — is written once, in the workshop:
[`hausfold/workshop` → `.agents/README.md`](https://github.com/hausfold/workshop/blob/main/.agents/README.md).
The table below is only what's wired in *this* repo.

| Path | Read by | What it actually is |
|---|---|---|
| `AGENTS.md` | Codex, OpenCode, Cursor, Zed, Amp, Copilot-in-editor, and anything else that speaks [agents.md](https://agents.md) | **The source of truth.** Every project rule. |
| `CLAUDE.md` | Claude Code (CLI, desktop, web) | `@AGENTS.md` import + a table of Claude-only wiring. Claude Code reads only `CLAUDE.md`, so the import is how it gets the real file. |
| `GEMINI.md` | Gemini CLI | Symlink → `AGENTS.md`. |
| `opencode.json` | OpenCode | Names `AGENTS.md` explicitly. Belt and braces — OpenCode finds it anyway. |
| `.github/copilot-instructions.md` | GitHub Copilot coding agent + code review | A **real file**, not a symlink: Copilot reads through the GitHub API, where a symlink is just a path string. |

**No session hook here, on purpose.** Every other repo in the family carries
`.agents/setup.sh` — a Nix bootstrap for bare cloud containers. This repo has no
flake, no build and no tests: it's a README. There is nothing to bootstrap, so
there's no `.agents/setup.sh`, no `.claude/settings.json`, no `.codex/` and no
`.opencode/plugins/`. That absence is a decision, not an oversight — if this
repo ever grows a build step, add the shared script from the workshop rather
than writing a second one.

Likewise no repo-local flows: the cross-repo ones (`/ship`, `/docs-sync`) belong
to the workshop. If one ever belongs here it goes in
`.agents/skills/<name>/SKILL.md`, symlinked into `.claude/skills/<name>/` and
`.opencode/skills/`, never copied.

## Caveat worth knowing

`.github/copilot-instructions.md` in **this** repo is a `.github` directory
*inside the repo named `.github`* — that reads oddly but is correct: Copilot
looks for the file at that path relative to a repo's root, and this repo's root
is the root. It does not make the file org-wide.
