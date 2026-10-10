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
