# 0005. Maven as the backend build tool

- **Status:** Accepted
- **Date:** 2026-11-23

## Context
The Spring Boot backend ([ADR 0004](0004-backend-java-spring-boot.md)) needs a
build tool for dependency management, testing and packaging. Spring Boot
supports both Maven and Gradle first-class.

## Decision
We will use **Maven**, invoked through the **Maven Wrapper** (`backend/mvnw`),
with the Maven version and its SHA-256 checksum pinned in
`backend/.mvn/wrapper/maven-wrapper.properties`.

## Alternatives considered
- **Gradle (Kotlin DSL)** — faster incremental builds and more flexible, but
  build logic is code, which adds a second thing to learn and debug. Build
  speed is not a bottleneck for a single service this size.

## Consequences
- Declarative `pom.xml` that most Java developers and CI templates understand.
- Contributors and CI need only a JDK. The wrapper fetches the exact Maven version.
- If the mobile app uses Android/Gradle, the repo will contain two build tools.
  This is acceptable because each lives in its own directory ([ADR 0001](0001-monorepo.md)).
