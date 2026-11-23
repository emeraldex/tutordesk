# TutorDesk backend

Spring Boot REST API. See [ADR 0004](../docs/adr/0004-backend-java-spring-boot.md)
and [ADR 0005](../docs/adr/0005-maven-build-tool.md).

## Prerequisites
- JDK 25 (e.g. [Eclipse Temurin](https://adoptium.net/)), with `JAVA_HOME` set.
- No Maven install needed: the wrapper (`mvnw`) downloads the pinned version.

## Common commands
Run from this `backend/` directory (use `mvnw.cmd` instead of `./mvnw` in cmd/PowerShell):

| Task | Command |
|---|---|
| Run tests | `./mvnw test` |
| Start the API on :8080 | `./mvnw spring-boot:run` |
| Build a runnable jar | `./mvnw package` |

Health check: <http://localhost:8080/actuator/health> should return `{"status":"UP"}`.
