# Architecture

Current truth, kept compact.

## What it is

A static site published by GitHub Pages at a single custom domain. It exists to
serve small machine-readable policy files, chiefly the MTA-STS policy that
tells sending mail servers to require TLS when delivering to the domain. There
is no server code and no build step.

## The stack (and why)

- **GitHub Pages, legacy build, source `main` at `/`.** Read from the repo's
  Pages settings, which are not in git. Static files and a fixed policy need
  nothing more.
- **`CNAME`** holds the custom domain; **`.nojekyll`** turns Jekyll off so the
  `.well-known/` directory is served as it stands.
- **HTTPS is enforced** by Pages for the custom domain, which MTA-STS needs.

## Layout

```
index.html           # the welcome page at the site root
.well-known/         # mta-sts.txt (the policy) and index.html (an explainer)
CNAME, .nojekyll     # Pages custom domain, Jekyll off
docs/                # this file, ROADMAP (generated) + roadmap/, sessions/
.githooks/           # tracked scan hooks (installed per clone, see CONTRIBUTING)
```

The site is served from the root, not a `site/` subfolder, because the Pages
source is the root. Everything at the root, `docs/` included, is therefore
served too.

## Testing

CI is atelier's scanner floor (`.github/workflows/floor.yml`), which checks the
tree for secrets, personal data, broken links and record hygiene. It does not
check that the site is live or that the MTA-STS policy validates for the
domain: that is a manual check against the deployed URL.

<!-- TODO: record how the policy is validated and its current mode once the
     owner says; this repo's history does not say. -->
