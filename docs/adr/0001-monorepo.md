# 0001. Monorepo

- **Status:** Accepted
- **Date:** 2026-11-22

## Context
TutorDesk has at least two deployable parts — a backend API and a mobile app —
plus design documents. It is built and maintained by one developer. Features
will usually touch the API and the client at the same time (e.g. adding a
lesson field means a schema change, an endpoint change and a UI change).

## Decision
We will keep all code and documentation in a single repository:

```
backend/   API and server-side code
mobile/    mobile client
docs/      ADRs and design documents
.github/   issue templates, PR template, CI workflows
```

## Alternatives considered
- **One repository per component** — cleaner separation, but cross-cutting
  changes need coordinated PRs across repos and versioned API contracts from
  day one. That overhead isn't worth it for a solo project.

## Consequences
- A single PR can change the API and its client together, so they never drift apart.
- One issue tracker, one project board, one history to read.
- CI must use path filters so a docs-only change doesn't trigger backend and
  mobile builds.
- `.gitignore` and `.editorconfig` must cover every toolchain used in the repo.
