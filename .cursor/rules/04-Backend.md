---
description: .NET 10 + EF Core 10 backend conventions
globs: src/backend/**/*
alwaysApply: false
---

# Backend

.NET 10 · EF Core 10 · MediatR · FluentValidation · xUnit/Moq

## Before Writing Code

1. Search existing Commands, Queries, Handlers, Repositories, DTOs, and `Shared/` utilities.
2. Mirror folder/naming patterns in the target use-case area.
3. Extend existing repos/handlers — don't duplicate logic.

## Projects (`net10.0`)

`ReviewSystem.{Domain,Application,Infrastructure,API,Shared}` — tests in `tests/backend/`

## Domain

Zero framework deps · factory methods + behavior methods · domain exceptions · one aggregate per repository

## Application

Per use case: `{Command|Query}.cs` + `Handler.cs` + `Validator.cs`

- Interfaces only in handlers (`IReviewRepository`, `IUnitOfWork`).
- Commands mutate + `SaveChangesAsync` in handler; queries → DTOs.
- `CancellationToken` on all async methods.

## Infrastructure

`ApplicationDbContext` · `IEntityTypeConfiguration<T>` in `Data/Configurations/` · `AsNoTracking()` reads · DI in `DependencyInjection.cs`

Migrations: `dotnet ef migrations add {Name} --project ReviewSystem.Infrastructure --startup-project ReviewSystem.API`

## API

`ISender` only · `api/v1/{resource}` · `[ProducesResponseType]` · no try/catch (middleware handles)

Exceptions: NotFound→404 · BusinessRule→409 · Validation→400 · `{ code, message, details }`

## Tests

Update `tests/backend/` when handler, validation, or endpoint behavior changes.

## Forbidden

`DbContext` in controller/handler · EF on domain entities · entities in API responses · logic in controllers · sync I/O · raw SQL in handlers · `SaveChanges` in repo · new NuGet packages without approval
