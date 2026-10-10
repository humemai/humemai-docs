# AGENTS.md: humemai-docs

This repository is the published branch of https://docs.humem.ai. Read `README.md` first: it says what is written by the project deploy workflows and what is edited by hand ("How the hub is written"), how the landing page takes its look from `brand/`, and the link rule that a doc page needs `/latest/` or a version.

## Rules for agents

- Never edit `brand/` in place: change the design system (`humemai/design-system`), vendor it again, and run `brand/verify.sh`.
- Never hand-edit a project folder the deploy workflows write.
- Update `README.md` in the same pull request as any change it describes, and remove the old text in that change.
- Stage files by explicit path. Delete the branch on merge. Issue, PR and comment bodies have no hard wraps and no em dashes. Always pass `-R` to `gh`.
- Work on a PR branch in a separate worktree (`git worktree add --detach <dir> origin/main`, then `git switch -c <branch>`), not by switching the main checkout: other agents and long runs use it.
- `gh pr edit` can exit 1 on the "Projects (classic)" error and leave the body unchanged. Use `gh api --method PATCH repos/OWNER/REPO/pulls/N -f body=...` and read the body back.
- This repository is public: no secrets, token locations or private notes.
