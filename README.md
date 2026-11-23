# TutorDesk

> <ONE sentence: what it is, for whom. ≤ 20 words.>

![Status](https://img.shields.io/badge/status-phase%200%20setup-lightgrey)
![License](https://img.shields.io/badge/license-PolyForm%20Noncommercial-blue)

## The problem
<2–3 sentences. The tutor's pain today, in concrete terms:
WhatsApp + Google Calendar + spreadsheets + bank-transfer screenshots.
Why existing tools don't fit (built for centres / USD pricing, no local payments).>

## The solution
<1 sentence summary, then 5–7 bullets of MVP features — user-facing
language, not tech language.>

## Who it's for
- **Solo private tutors** in Malaysia — <one line>
- **Parents** — <one line: no app to install>

## Status
🚧 **Phase 0 – Setup.** See the [project board](<link>) and [roadmap](#roadmap).

## Tech stack
- **Backend:** Java 25 + Spring Boot 4.2, built with Maven ([ADR 0004](docs/adr/0004-backend-java-spring-boot.md), [ADR 0005](docs/adr/0005-maven-build-tool.md))
- **Mobile:** _to be decided_
- **Database / hosting:** _to be decided in Phase 3_

## Architecture
_Coming in Phase 3._

## Getting started
- **Backend:** see [backend/README.md](backend/README.md).
- **Mobile:** _coming later._

## Testing
_Coming in Phase 5._

## Key decisions
| ADR | Decision |
|---|---|
| [0001](docs/adr/0001-monorepo.md) | Monorepo |
| [0002](docs/adr/0002-trunk-based-development.md) | Trunk-based development |
| [0003](docs/adr/0003-source-available-licence.md) | PolyForm Noncommercial licence |
| [0004](docs/adr/0004-backend-java-spring-boot.md) | Backend in Java with Spring Boot |
| [0005](docs/adr/0005-maven-build-tool.md) | Maven as the backend build tool |

## Roadmap
- [x] Phase 0 – Setup
- [ ] Phase 1 – Planning
- [ ] Phase 2 – Requirements
- [ ] Phase 3 – Design
- [ ] Phase 4 – Implementation
- [ ] Phase 5 – Testing
- [ ] Phase 6 – Deployment
- [ ] Phase 7 – Operations
- [ ] Phase 8 – Portfolio packaging

## Licence
Source-available under the [PolyForm Noncommercial License 1.0.0](LICENSE).
You may read, run and modify the code for non-commercial purposes.
Third-party dependencies remain under their own licences.