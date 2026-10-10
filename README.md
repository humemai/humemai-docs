# humemai-docs

Shared documentation hub for published HumemAI project docs.

Current doc sets:

- `arcadedb/`
- `humemdb/`
- `dbbench/`
- `cypherglot/`
- `audit-ready-memory/`

The landing page (`index.html`) takes its colours, type, logo and favicon from the HumemAI design system, vendored into `brand/` from [humemai/design-system](https://github.com/humemai/design-system) (`brand/verify.sh` checks the copy). Each doc set's own theme is vendored in its source repo, under `docs/brand`.

Versions published before the design system (up to arcadedb 26.9.1, humemdb 0.1.0.dev4, cypherglot 0.1.0 and audit-ready-memory 0.0.2) were restyled in place on 2026-09-27 with the design system's `scripts/restyle-built-mkdocs.py`: theme only, page text unchanged. `favicon.ico` at the root answers browsers that ask for it on any page.

## How the hub is written

Each project's own repository builds its docs, and its deploy workflow pushes them here with mike under `<project>/<version>/` and an alias `latest`; the bot commits read "Deployed <sha> to <version> in <project>". The project folders are written by those workflows: do not edit or delete them by hand (the restyle script above is the one exception, for old versions). What is edited by hand is `index.html`, `README.md`, `favicon.ico`, `CNAME` and, through the design system, `brand/`.

- A link to a doc page needs the version segment: `https://docs.humem.ai/<project>/latest/<page>/` works and `https://docs.humem.ai/<project>/<page>/` is a 404. Only the project root `https://docs.humem.ai/<project>/` redirects.
- To add or remove a project, change its landing card in `index.html` and the list above in the same pull request, and keep both equal to the folders that exist. A new project's deploy workflow can be copied from `humemai/dbbench` and needs the `HUMEMAI_DOCS_TOKEN` secret.
- The bots push to `main` at any time: pull with rebase before you push, and never force-push.
- There is no CI here. Before you merge, open `index.html` in a browser at a wide desktop width and a phone width, in light and dark mode, and run `brand/verify.sh`.
