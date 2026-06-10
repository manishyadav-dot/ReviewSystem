---
description: Layer boundaries and cross-cutting concerns
alwaysApply: true
---

# Architecture

Clean Architecture · .NET 10 · EF Core 10 · MediatR CQRS · React SPA

## Dependency

```
API → Application → Domain
         ↑
   Infrastructure
```

| Layer | Project | Owns |
|-------|---------|------|
| Domain | `ReviewSystem.Domain` | Entities, enums, domain exceptions |
| Application | `ReviewSystem.Application` | Commands, queries, DTOs, interfaces, validators |
| Infrastructure | `ReviewSystem.Infrastructure` | EF Core, repositories, external services |
| API | `ReviewSystem.API` | Controllers, middleware, DI, Swagger |
| Shared | `ReviewSystem.Shared` | Constants, guards, shared types |

## Constraints

- **Domain:** No EF/ASP.NET/MediatR. Persistence-ignorant entities.
- **Application:** Interfaces only in handlers. DTOs out, never entities. FluentValidation before handlers.
- **Infrastructure:** EF Core only for DB. Fluent config in `Data/Configurations/`. `AsNoTracking()` on reads.
- **API:** `ISender` only in controllers. Exception middleware → HTTP.
- **FE:** `features/` isolated. HTTP via `services/` only.

## EF Core

Provider: `Microsoft.EntityFrameworkCore.SqlServer` · Migrations: `Infrastructure/Data/Migrations/` · Manual SQL: `src/database/migrations/` (keep synced)

## API

REST JSON `/api/v1/` · OpenAPI: `docs/API/openapi.yaml` · Breaking changes → `/api/v2/` + ADR

## Cross-Cutting

Auth: API middleware · Logging: `ILogger<T>` + correlation ID · Errors: `{ code, message, details }` · Secrets: Key Vault

## Lifecycle

Component → `services/` → Controller → MediatR → Repository → EF Core → SQL Server → DTO

## ADRs

`docs/Architecture/adr/NNNN-title.md` for framework changes, new patterns, breaking APIs.
