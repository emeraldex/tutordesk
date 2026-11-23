# 0006. PostgreSQL as the database

- **Status:** Accepted
- **Date:** 2026-11-23

## Context
TutorDesk's core data is relational and must stay consistent:

- a **tutor** has many **students**, and a student may have one or more **parents**;
- **lessons** link a tutor and a student at a point in time, and may recur weekly;
- **payments** settle one or more lessons and must never be lost or double-counted.

Queries are mostly relational: "this week's lessons", "unpaid lessons for this
student", "income this month". The backend is Spring Boot ([ADR 0004](0004-backend-java-spring-boot.md)),
so the database must be well supported by Spring Data JPA. It must also be
available as a cheap or free managed service, and testable locally.

## Decision
We will use **PostgreSQL 18** as the single system of record, with:

- **Spring Data JPA (Hibernate)** for data access;
- **Flyway** for versioned schema migrations in
  `backend/src/main/resources/db/migration`, with Hibernate set to
  `ddl-auto: validate` so it never changes the schema itself;
- **Testcontainers** so integration tests run against a real PostgreSQL 18 in
  Docker, both locally and in CI. No H2 or other stand-in database.

## Alternatives considered
- **MySQL / MariaDB** — equally capable for this workload, but PostgreSQL has
  richer types (`timestamptz`, ranges, `jsonb`), partial indexes and check
  constraints that suit scheduling and payment rules.
- **MongoDB / Firestore (document stores)** — flexible schemas, but our data is
  relational and payments need multi-row transactions and foreign keys.
- **H2 for tests, PostgreSQL in production** — faster tests, but SQL dialect
  differences hide bugs until production. Testcontainers removes that gap.
- **PostgreSQL 19** — released 2026-11-19. We'll wait until the chosen hosting
  provider supports it, then upgrade in a separate PR.

## Consequences
- **Schema changes go through Flyway only.** Every change is a new
  `V<n>__<description>.sql` file. Migrations that have been merged are never edited.
- **Docker is required** to run integration tests and the local database
  (via a `compose.yaml` in `backend/`). CI's `ubuntu-latest` runners already have Docker.
- **Conventions:**
  - **Money:** `NUMERIC(12,2)` in MYR, mapped to `BigDecimal`. Never floating point.
  - **Instants:** `timestamptz`, stored in UTC. Display uses the tutor's time
    zone (default `Asia/Kuala_Lumpur`).
  - **Recurring lessons:** a recurrence rule plus generated lesson rows, so
    each lesson can be paid, rescheduled or cancelled individually.
  - **Primary keys:** UUIDs, so IDs in parent-facing links can't be guessed.
- **Hosting is still open.** The provider must offer managed PostgreSQL 18 with
  automated backups (decided in the hosting ADR).
