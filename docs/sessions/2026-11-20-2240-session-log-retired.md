# 2026-11-20 · 2240 UTC · One-file session log retired into the folder

A headless health-sweep session, started inside this repo's worktree.

## Why

The house record standard keeps the session log as the `docs/sessions/` folder
alone, with no index file beside it. This repo still had `docs/SESSIONS.md`.

## What changed

- `docs/SESSIONS.md` retired with atelier's `archivecut.py`. Its one entry now
  sits, word for word, in the session file it linked; its preamble is kept
  word for word in `docs/sessions/README.md`, below the tool's marker.
  The last commit touching the file was `3a57e47`.
- `docs/sessions/README.md` added by the tool: it explains the folder form.
- `.wrapscanignore`: dropped the line for the removed index; the folder glob stays.
- There is no frozen pre-split roadmap or session archive here, so the
  archive step had nothing to cut.

## Checks

- `archivecut.py --plan` and `--cut`: every proof line PASS.
- `board.py --check`: index current.

## Observations (not work items)

- This repo has no `CLAUDE.md` onramp, so there was no read order or closing
  rule to reword; nothing else pointed at the old index.
