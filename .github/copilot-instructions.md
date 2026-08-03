# Copilot instructions

**Read [`AGENTS.md`](../AGENTS.md) at the repo root first — it is the full,
authoritative instruction set for every agent working here, and this file is
only a pointer to it.** (Copilot doesn't follow file imports, hence the
duplication below; if the two ever disagree, `AGENTS.md` wins.)

The short version:

- This is `nebelhaus/.github` — the **org front page**, and nothing else. It
  ships no code and no flake; downstream pins nothing here.
- **GitHub renders `profile/README.md`, not the repo root `README.md`.** That's
  the only file that reaches <https://github.com/nebelhaus>.
- **Images are self-hosted via `raw.githubusercontent.com`**, so the URL carries
  the branch and the exact filename. Replacing an image while renaming it 404s
  the org page — keep `profile/assets/nebelhaus-family-showcase.png` as the name.
- The README is a **router, not documentation**: one line per repo, depth lives
  on nebelhaus.com and in each tool's own README.
- A rebrand spans **three repos** — the tool's own assets, `workshop/web/`, and
  the family showcase tile here. A PR touching only one of them leaves the
  family visibly inconsistent.

For review comments, the same bar applies as anywhere in the family:
correctness and boundaries (does this change belong in *this* repo?) over style.
