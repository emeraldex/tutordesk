# 0004. Backend in Java with Spring Boot

- **Status:** Accepted
- **Date:** 2026-11-23

## Context
TutorDesk needs a backend API for tutors' schedules, students, lessons and
payments, and for the parent-facing views (which need no app install). The backend must:

- handle relational data with integrity guarantees (lessons ↔ students ↔ payments);
- authenticate tutors and give parents scoped, low-friction access;
- integrate with local payment providers and send notifications;
- be maintainable by one developer and showcase skills relevant to the
  Malaysian job market, where Java/Spring is widely used in enterprise and fintech.

## Decision
We will build the backend in **Java (current LTS, 25)** using **Spring Boot**, in
`backend/`. We'll use the standard Spring ecosystem where it fits:
Spring Web for the REST API, Spring Data JPA for persistence, Spring Security
for authentication and authorisation, and Bean Validation for input checks.

## Alternatives considered
- **Node.js (NestJS / Express)** — fast to start and shares a language with web
  front-ends, but weaker static typing and less alignment with target employers.
- **Kotlin + Spring Boot** — same ecosystem with more concise code. Rejected for
  now to keep the backend in the most widely hired-for language. It can be revisited later.
- **Backend-as-a-service (Firebase / Supabase)** — least code, but payment-provider
  integration and complex business rules end up in clients or cloud functions,
  and it showcases fewer backend skills.

## Consequences
- Mature, well-documented libraries for security, persistence, scheduling and testing.
- Higher memory footprint and slower cold starts than Node or Go. Hosting must
  allow a long-running JVM instead of scale-to-zero functions.
- Follow-up decisions needed (separate ADRs): build tool (Maven vs Gradle),
  database (likely PostgreSQL), parent-facing access method, and hosting.
- The mobile client stack is **not** decided by this ADR.
