# AGENTS.md: humemai-docs

This repository is the published branch of https://docs.humem.ai. Each project's own repository builds its docs and a deploy workflow pushes them here with mike under `<project>/<version>/` and an alias `latest`; the bot commits read "Deployed <sha> to <version> in <project>".

## What you edit by hand

- `index.html` (the landing page), `README.md`, `favicon.ico`, `CNAME`.
- `brand/` is vendored from `humemai/design-system`. Never edit it in place: re-vendor from the design system and run `brand/verify.sh`.
- Project folders (`arcadedb/`, `humemdb/`, `cypherglot/`, `audit-ready-memory/`, `dbbench/`) are written by the deploy workflows. Do not edit or delete them by hand, except with the design system's restyle script for old versions.

## Rules

- Links to a doc page include the version segment: `https://docs.humem.ai/<project>/latest/<page>/` works, `https://docs.humem.ai/<project>/<page>/` is a 404. Only the project root `https://docs.humem.ai/<project>/` redirects.
- Adding or removing a project: change the landing card in `index.html` and the "Current doc sets" list in `README.md` in the same pull request, and keep both equal to the folders that exist. Use the deploy workflow of `humemai/dbbench` as the template for a new project's workflow, which needs the `HUMEMAI_DOCS_TOKEN` secret.
- Bots push to `main` at any time. Pull with rebase before you push, and never force-push.
- There is no CI here: before you merge, open `index.html` in a browser at a wide desktop width and a phone width, in light and dark mode, and run `brand/verify.sh`.
- Stage files by explicit path. Delete the branch on merge. Issue, PR and comment bodies have no hard wraps and no em dashes. Always pass `-R` to `gh`.
- This repository is public: no secrets, token locations or private notes.
