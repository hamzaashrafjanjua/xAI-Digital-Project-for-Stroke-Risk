# Contributing and Collaboration Workflow

## Branching strategy
- Protect `main` (no direct pushes). All changes come via Pull Requests (PRs).
- Work on short-lived feature branches: `feature/<scope>` or `fix/<scope>`.
- Keep PRs small (≤300 LOC), single-topic, and merge to `main` frequently.

## Pull Request rules
- Rebase/update your branch on latest `main` before opening a PR.
- Resolve conflicts locally; do not use `--force` on shared branches.
- Require at least one reviewer and CODEOWNERS approval when touching owned paths.
- Require status checks: lint/tests pass; notebooks diff clean.

## Ownership and structure
- Use `CODEOWNERS` to assign reviewers for specific files/folders.
- Keep modules in separate folders to minimize overlap; avoid editing others’ owned areas.

## Notebooks: avoid merge pain
- We use `nbdime` merge/diff and strip outputs before commit to reduce conflicts.
- Install locally:
  ```bash
  pip install nbdime nbstripout pre-commit
  nbdime config-git --enable
  nbstripout --install
  pre-commit install
  ```
- Keep outputs cleared (Restart & Clear Output) before committing.

## Commit hygiene
- Write descriptive messages (`feat:`, `fix:`, `docs:`, `refactor:`).
- One logical change per commit; avoid committing generated artifacts.

## CI expectations
- Unit tests and lint/type checks must pass.
- Optional: notebook smoke test (import/runtime sanity).

## Release/merge policy
- Prefer "Require branches to be up to date before merging" in GitHub settings.
- Use squash merges for noisy branches; merge commits acceptable for multiple contributors.
