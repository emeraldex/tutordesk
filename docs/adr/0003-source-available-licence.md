# 0003. PolyForm Noncommercial licence

- **Status:** Accepted
- **Date:** 2026-11-22

## Context
TutorDesk is a portfolio project, so the source must be public and readable by
recruiters and other developers. It is also a product idea with commercial
potential, so others shouldn't be able to take the code and sell it as a
competing service.

## Decision
We will release the code under the
[PolyForm Noncommercial License 1.0.0](https://polyformproject.org/licenses/noncommercial/1.0.0/).
Anyone may read, run, modify and share it for non-commercial purposes;
commercial use requires separate permission from the copyright holder.

## Alternatives considered
- **MIT / Apache-2.0** — maximises reuse, but allows anyone to commercialise the product.
- **AGPL-3.0** — open source with strong copyleft. It still allows commercial
  hosting by others, as long as they publish their changes.
- **No licence (all rights reserved)** — legally prevents even reading-and-running,
  which undermines the portfolio goal.

## Consequences
- The project is **source-available, not open source** (by the OSI definition).
  The README and any public descriptions must say so accurately.
- Outside contributions would need a contributor agreement if commercial use is
  ever pursued. Until then, contributions are not actively solicited.
- Third-party dependencies remain under their own licences. Their licences must
  be compatible with distributing TutorDesk under PolyForm Noncommercial
  (permissive licences such as MIT/Apache-2.0/BSD are fine).
