---
description: Project scope, stack, paths, docs
alwaysApply: true
---

# Project Overview

**ReviewSystem** — enterprise review management platform. Monorepo, early scaffold.

## Stack

| Layer | Tech | Path |
|-------|------|------|
| Frontend | React, TypeScript, Vite | `src/frontend/` |
| Backend | .NET 10, EF Core 10, MediatR | `src/backend/` |
| Database | SQL Server | `src/database/` |
| Tests | Vitest, Playwright, xUnit | `tests/` |
| DevOps | Docker, GitHub Actions | `devops/` |
| Docs | Markdown | `docs/` |

## Data Flow

`Frontend → /api/v1/ → CQRS → EF Core 10 → SQL Server`

## Key Paths

- FE: `src/frontend/src/{components,features,services,hooks,store,types,utils,config}/`
- BE: `src/backend/src/{API,Application,Domain,Infrastructure,Shared}/`
- EF migrations: `Infrastructure/Data/Migrations/` · SQL scripts: `src/database/migrations/`

## Docs

`docs/{PRD,Architecture,Database,API,UIUX,BusinessRules,DevOps,Standards,Onboarding}/`

## Environments

Dev (`develop`) · Staging (`release/*`) · Production (`main`) — config in `devops/environments/`

## Scope

**In:** Requested features + supporting tests/docs. **Out:** Login, Dashboard, stack swaps, speculative scope, unrelated refactors.
