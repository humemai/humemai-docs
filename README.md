# humemai-docs

Shared documentation hub for published HumemAI project docs.

Current doc sets, each with a card on the landing page:

- `dbbench/`
- `audit-ready-memory/`

Unlisted (no card, files kept so existing links and the packages' own links keep working): `humemdb/` and `cypherglot/`, paused projects, hidden from the landing page on 2026-10-19 as on humem.ai.

Retired: `arcadedb/`, the docs of the old `arcadedb-embedded` package. Since 2026-10-29 every path under `docs.humem.ai/arcadedb` (root, `latest` and the version folders) redirects to https://docs.arcadedb.com/arcadedb-python/ through a Cloudflare Single Redirect rule on the humem.ai zone (302 for the first week, then 301). The files stay in this repository; they are no longer reachable at their old URLs. The landing page keeps an "ArcadeDB Python" card that links straight to https://docs.arcadedb.com/arcadedb-python/ (an external card, no folder here).

The landing page (`index.html`) takes its colours, type, logo and favicon from the HumemAI design system, vendored into `brand/` from [humemai/design-system](https://github.com/humemai/design-system) (`brand/verify.sh` checks the copy). Each doc set's own theme is vendored in its source repo, under `docs/brand`.

Versions published before the design system (up to arcadedb 26.9.1, humemdb 0.1.0.dev4, cypherglot 0.1.0 and audit-ready-memory 0.0.2) were restyled in place on 2026-09-27 with the design system's `scripts/restyle-built-mkdocs.py`: theme only, page text unchanged. `favicon.ico` at the root answers browsers that ask for it on any page.

## How the hub is written

Each project's own repository builds its docs, and its deploy workflow pushes them here with mike under `<project>/<version>/` and an alias `latest`; the bot commits read "Deployed <sha> to <version> in <project>". The project folders are written by those workflows: do not edit or delete them by hand (the restyle script above is the one exception, for old versions). What is edited by hand is `index.html`, `README.md`, `favicon.ico`, `CNAME` and, through the design system, `brand/`.

- A link to a doc page needs the version segment: `https://docs.humem.ai/<project>/latest/<page>/` works and `https://docs.humem.ai/<project>/<page>/` is a 404. Only the project root `https://docs.humem.ai/<project>/` redirects.
- To add, remove, hide or show a project, change its landing card in `index.html` and the lists above in the same pull request: every folder is either listed with a card or named as unlisted. A new project's deploy workflow can be copied from `humemai/dbbench` and needs the `HUMEMAI_DOCS_TOKEN` secret.
- The bots push to `main` at any time: pull with rebase before you push, and never force-push.
- There is no CI here. Before you merge, open `index.html` in a browser at a wide desktop width and a phone width, in light and dark mode, and run `brand/verify.sh`.
