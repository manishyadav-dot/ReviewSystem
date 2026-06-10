---
description: File placement rules
alwaysApply: false
---

# Folder Structure

See `01-Project-Overview.md` for full path map.

## Placement

| What | Where |
|------|-------|
| New FE feature | `src/frontend/src/features/{name}/` |
| Shared UI | `components/common/` or `components/layout/` |
| API calls | `services/` |
| BE use case | `Application/Commands|Queries/{UseCase}/` |
| Domain entity | `Domain/Entities/` |
| EF config | `Infrastructure/Data/Configurations/` |
| SQL script | `src/database/migrations/` |
| Tests | `tests/{layer}/` — mirror source, never inside `src/` |

## Rules

- Search existing folders before creating new ones.
- Shared across features → `components/`, `hooks/`, `services/` — not inside a feature.
- No parallel structures — use what exists. New top-level folders need ADR.

## Forbidden

Code in repo root · tests in `src/` · feature code outside `features/` · business logic in `components/common/`
