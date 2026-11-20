<!-- stamp:begin source=docs/method/PROPAGATION.md region=floor -->
## Doctrine — inherited from atelier (pinned `atelier@0c6db458`)

This repo works by the atelier operating model. The safety floor here is
**inlined so it binds even if atelier is never read**; all richer doctrine lives
in atelier and is read on demand — never wholesale.

- **The apex (never traded, any model):** Honesty is absolute — never a claim
  stronger than its evidence; report what broke *first*; "done" means verified,
  not "looks right". Then adaptation — learn and improve yourself and your tools
  as you work; it sits below honesty because adaptation runs on evidence, and
  honesty is what makes the evidence trustworthy. Surface a genuine dilemma;
  never silently resolve it — a quietly picked fork is a withheld truth.
- **Always stop and confirm (the floor):** making a private repo public or
  widening its audience; anything truly destructive or irreversible; bulk
  deletion from a record store, meaning the roadmap, session logs, ADRs or
  reviews, whoever wrote it, shown first because recoverable bytes are the
  wrong test there; secrets; spending money; anything touching people's safety;
  widening your own grant
  (record the principal's decision, never originate it); a lockout-class change
  that could sever your own access; installing an unapproved tool or adding a
  new trust surface (deploy keys, webhooks, OAuth/app grants). Each such
  confirmation is an *informed* one — the agent gives the full account
  `00-APEX.md` owes, in plain language, first. The principal's authority is
  absolute — never overrule him, even if you believe him uninformed; an approval
  given without that account is open to challenge on the briefing, and the
  challenge is raised to him by re-briefing (`00-APEX.md`) — and at *this*
  floor the re-briefing comes **before** the action, never after it, because
  what the floor guards cannot be taken back. Everything
  else recoverable — commit/push/PR included — just proceed.
- **Asking — any question, decision or ruling:** put the ask in the harness's
  structured question device where one exists (Claude Code:
  `AskUserQuestion`), never buried in prose; with no device (a non-interactive
  run, a scheduled batch, a harness without one) the same content goes in
  prose. The account must have *reached* the principal before the choice is
  put — always written out as text first, then the device carries the choice
  alone, in the same turn; never end the turn between them — and never trim
  the account to fit. Give the real options, each with its pros, cons,
  impacts, risks, costs and any other consideration that bears on the choice,
  plus **a recommendation** with its reasoning shown. Every fact in the ask is
  verified, or plainly marked as assumed where verifying would cost more than
  the decision is worth.
  (`00-APEX.md` for what an ask must contain; `COMMUNICATION.md` § *Asking for
  a ruling* for how it travels.)
- **Concurrency:** assume another session may be live — a clean tree is not
  proof you're alone. At session start run `cclive` where it is installed
  (every live session, claim and worktree on this machine, about 2 s), and
  read `git status` first — dirty work
  this session didn't make means stop and move, never autostash it — then,
  where the branch has an upstream, `git pull --rebase --autostash`; push after each
  commit. Take a worktree by default for write-heavy or multi-commit
  work; uncommitted changes this session didn't make are positive proof ⇒ move
  to a worktree — never work around or absorb them (`CONCURRENCY.md`). Name
  records (session logs, ADRs, reviews) coordination-free —
  `YYYY-MM-DD-HHMM-slug.md`, `HHMM` in UTC (`date -u`); never a next-N counter;
  files named under retired schemes keep their names. Where sessions can message
  each other, announce your **file set** on open and answer peers' — a claim says
  what, never which files. A message reserves nothing; only a pushed artefact
  does, so check a shared allocator (identifiers, version constants) **after**
  the push. The shared checkout's index and its mid-rebase state are shared
  surfaces too: stage explicit paths, never `git add -A`, and read the **whole
  staged index** before every commit — `git diff --cached` shows the paths you
  did not stage as well, which is the half a hunk-by-hunk read misses
  (`CONCURRENCY.md` § The trigger).
- **Session rhythm (points up for the full rule):** claim work you take off the
  shared queue before starting it, and let a live `[~]` claim override a
  standing instruction to take that item; stay in the lane you were given
  (`CONCURRENCY.md`); flag when economics favour a fresh session, and on
  overload stop at a safe point, record, and hand off (`ECONOMICS.md`);
  before you declare the work wrapped, do the put-away unprompted and close
  with an evidence-based all-clear that nothing owed is left uncaptured
  (`RECORD.md`).
- **Doctrine problems point up (every repo, atelier included):** if a house rule
  is wrong, unworkable, ambiguous, contradictory, stale, missing or unfindable,
  **report it to atelier** — with evidence where evidence exists, marked
  unevidenced where it does not. Consideration and remediation are atelier's;
  the reporting session stops at the report and never silently works around a
  rule it thinks is wrong, because the workaround destroys the only evidence the
  house would get. Check the parent's actual file first — this block is a lossy
  summary and is not evidence about what the house says. File it in atelier's
  board directly, or hand it over the peer channel, or — where neither is
  reachable — hold it in this repo's record marked owed upstream. Describe the
  problem by its class only: atelier is public and a push cannot be retracted,
  so a private repo never names itself or its contents (hosts, clients,
  secrets) on the branch, PR title, commit subject, PR body or item. Filing
  without harming the parent: name the branch for the report, say it is a
  hand-up in the first line, open the PR before you stop, and touch nothing but
  your own item. (`PROPAGATION.md` § *Pointing up*.)
- **Source & drift:** canonical doctrine is `../atelier/docs/method/`. At
  session start run `A="${ATELIER_TOOLS:-$(git config hooks.atelierTools)}/..";
  git -C "$A" fetch -q && git -C "$A" log --oneline 0c6db458..origin/main` — the
  parent's published mainline (its remote is assumed to be `origin`), never
  whatever branch its checkout is parked on. The path comes from the hooks'
  tools setting, never `../`, so it resolves from a worktree too. A failed
  command is *no result*, not *no drift*; any output means the house doctrine
  moved — read it, then bump the pin above deliberately.
- **Estate resources — one home, the estate root:** providers & account plans,
  financial constraints & plan entitlements, licences, credentials and the
  estate inventory live in the operator's **private estate-root repo**
  (atelier's private counterpart) and nowhere else. Every other repo reads them
  there, never re-derives them or copies the root's contents down, and writes a
  fact of this kind it learns (an invoice, a mail, a provider's page, the
  principal's word; never a secret's value) up to the root with its source and
  date; where the root cannot be reached, it holds the fact in its own record
  marked owed to the root. The **expected toolbox** (which tools to expect, and
  how to find them) is atelier's: `method/TOOLBOX.md`. The root is a private
  repo like any other: it may be named, and in a public tree what it holds and
  its condition go by type only (`RECORD.md` § *The record is public*).
- **This repo's visibility:** PUBLIC (every push is publication, and GitHub Pages serves the default branch's root as a live site).
  Verify: `gh repo view mike548141/cel-web-hosting --json visibility`.
<!-- stamp:end -->

---

# cel-web-hosting — session onramp

A small static site served by GitHub Pages: a welcome page and the MTA-STS
policy under `.well-known/`.

## Read order at session start

1. `docs/ARCHITECTURE.md` — current truth: what is served and how.
2. `docs/ROADMAP.md` — what's open.
3. The newest few files in `docs/sessions/` — where the last sessions left off
   (`ls docs/sessions/[0-9]* | tail -5`; the folder is the session log, one
   file per session, named for its start). A last commit
   then silence with no closing session file means the last session either died
   mid-flight or is still live — run the read-first recovery sweep
   (`../atelier/docs/method/CONCURRENCY.md` § Surviving an interrupted
   session) before assuming either. A cold reviewer skips this step: the log is
   on the review rules' barred list (`../atelier/docs/method/REVIEW.md`
   rule 2).

## Hard constraints

- **Everything at the repo root is published twice over.** The repo is public,
  and GitHub Pages serves the default branch's root (`.nojekyll` is present, so
  nothing is filtered out). A file added here is readable at the site's URL as
  well as on GitHub. Keep the served files, `CNAME` and `.well-known/` exactly
  as they are unless the task is to change them; never add a secret, a draft or
  anything not meant to be read by anyone.
- **`.well-known/mta-sts.txt` is policy, not content.** Its `mode` and `max_age`
  change how other mail servers treat this domain's mail. Changing them is the
  owner's decision, never a session's.
- **Pages settings are not in git.** Source branch and path, custom domain and
  HTTPS enforcement live in the GitHub repo settings. Changing them is a floor
  action (a new trust surface or an audience change): describe it, don't do it.
- **Personal data only for a purpose, and every exception recorded.** This repo
  avoids PII by default: real people's names, contact details and addresses,
  health, family and financial detail, and any identifier that points at one
  person (an account name). Estate detail (hostnames, topology, machine-local
  paths, client names) is not PII, but the same default and recording apply.
  An exception stands only if the work this repo exists to do cannot be done
  without that very datum; one a placeholder or an invented example would serve
  fails. Each is recorded in `docs/PERSONAL-DATA.md` (the data, why, how it was
  granted, the files it may stand in); a repo whose list has no entries holds none. In
  a public repo only the principal grants an exception, in his own words, and
  the list is closed until he adds to it: a session that thinks it needs one
  stops and asks. An allow-marker on a line is not a grant, and the leak and
  secret scans catch the shape of personal data, not its purpose. Full rule:
  `../atelier/docs/build/REPO-STANDARD.md`.
- **Hooks don't travel.** The scan hook and its `hooks.atelierTools` config are
  per-clone — git transports neither, so a fresh clone commits **unscanned**
  until they're reinstalled. Before the first commit on any new clone or
  machine, rewire them (commands in CONTRIBUTING — Development setup).

## Layout

The site is served from the root because Pages is set to publish `main` at `/`;
that is the stated exception to the standard's product-in-a-subfolder rule.

- `index.html` — the welcome page.
- `.well-known/` — the MTA-STS policy (`mta-sts.txt`) and an explainer page.
- `CNAME`, `.nojekyll` — Pages custom domain, and Jekyll switched off.
- `docs/` — architecture, roadmap (`roadmap/` and the generated `ROADMAP.md`),
  session log (`sessions/`).
- `.githooks/` — the tracked scan hooks; `.github/workflows/floor.yml` is CI.

## Dev loop

There is no build. Open `index.html` in a browser to check the page. The checks
are atelier's floor, run by the hook on every commit and by
`.github/workflows/floor.yml` on every push.

## Conventions

- NZ English; macrons on te reo Māori.
- Comments say *why*, not *what*; ADR the re-litigable decisions
  (`docs/decisions/`); write the session's own file in `docs/sessions/`
  (`<date>-<HHMM>-<slug>.md`, start time in UTC) before finishing.
- Commit messages: `area: imperative subject`, why-dense body.
