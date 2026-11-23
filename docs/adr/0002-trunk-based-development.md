# 0002. Trunk-based development

- **Status:** Accepted
- **Date:** 2026-11-22

## Context
With one developer, long-lived feature or release branches add merge overhead
without any benefit from isolation. We still want every change to be reviewable
and to leave a clean, readable history for portfolio readers.

## Decision
- `main` is the trunk and must always build and pass tests.
- Work happens on short-lived branches (ideally merged within a day or two),
  named `<type>/<short-description>`, e.g. `feat/lesson-scheduling`.
- Every change reaches `main` through a pull request and is **squash-merged**,
  so each PR becomes one commit on `main`.
- Commit and PR titles follow [Conventional Commits](https://www.conventionalcommits.org/)
  (`feat:`, `fix:`, `docs:`, `chore:`, `refactor:`, `test:`, `ci:`).
- Unfinished features that must merge early are hidden behind a feature flag
  rather than kept on a long-lived branch.

## Alternatives considered
- **GitFlow** — `develop`/`release`/`hotfix` branches suit scheduled releases
  for teams. That is excess ceremony for a solo project.
- **Committing directly to `main`** — fastest, but loses the PR as a unit of
  review and a place to link issues.

## Consequences
- History on `main` is linear and reads like a changelog.
- Branch protection on `main` (require PR, require CI once it exists) should be enabled.
- Large features must be sliced into small, independently mergeable PRs.
