# 2026-11-20 · 2251 UTC · Adopted into atelier

A headless health-sweep session, started inside this repo's worktree, run in
atelier's `create-repo` standardise mode.

## Why

The repo had the scanner floor, the board and the session folder, but no
`CLAUDE.md` onramp, no atelier pin and no installed scan hook. The standing
rule is that every repo other than archives and forks works the house way.

## What changed

- `CLAUDE.md`: the onramp, with the doctrine block stamped at `atelier@0c6db458`
  (atelier's mainline at the time), the read order, and this repo's hard
  constraints. The main one is that the site is served from the root, so
  anything added there is published.
- `.githooks/` (`pre-commit`, `pre-merge-commit`, `commit-msg`): copied verbatim
  from atelier. `core.hooksPath` and `hooks.atelierTools` are set in this clone.
- `.gitignore`: from the template, which keeps `.claude/settings*.json` out of git.
- `CONTRIBUTING.md`: from the template, trimmed to what applies to a site with
  no build. It carries the once-per-clone hook setup.
- `docs/ARCHITECTURE.md`: written from what the repo and its Pages settings
  show; one `TODO` stub for how the MTA-STS policy is validated, which the
  history does not say.
- `docs/PERSONAL-DATA.md`: an empty closed list, which the public-repo check
  wants to find; no grant is invented.
- `docs/decisions/` and `docs/reviews/`: the template's READMEs, so the links
  in `CONTRIBUTING.md` resolve.

## Checks

- Pages source read from the GitHub API: legacy build, `main` at `/`, `.nojekyll`
  present, no `_config.yml`. Jekyll is off, so there is no exclude list to
  extend: every file at the root is served as it stands.
- `.atelier-floor.json` already existed and was left as it was.
- Served files, `CNAME`, `.well-known/`, the licence and history are untouched.
- The floor and the hook checks are on the commit below; CI results are in the
  session's final report.

## Observations (not work items)

- The new root files (`CLAUDE.md`, `CONTRIBUTING.md`, `.githooks/`) are now
  readable at the site's own address, as `docs/` already was. They are public
  on GitHub either way. Keeping them off the domain would mean moving the site
  into a subfolder and changing the Pages source: the owner's call.
- `.well-known/mta-sts.txt` still declares `mode: testing`; whether to move it
  to `enforce` stays the owner's decision.
