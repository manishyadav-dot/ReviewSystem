# Backend (.NET 10)

ASP.NET Core REST API following clean architecture principles.

## Tech Stack

- .NET 10 (ASP.NET Core Web API)
- Entity Framework Core 10 — ORM for SQL Server
- MediatR (recommended) — CQRS command/query dispatch
- FluentValidation (recommended) — Request validation

## Solution Structure

```
backend/
└── src/
    ├── API/              # HTTP controllers, middleware, filters
    ├── Application/      # Use cases, DTOs, interfaces
    ├── Domain/           # Entities, enums, domain exceptions
    ├── Infrastructure/   # EF Core 10, external services, repositories
    └── Shared/           # Cross-cutting utilities and constants
```

## Layer Dependencies

```
API → Application → Domain
         ↑
   Infrastructure
```

- **Domain** has no dependencies on other layers.
- **Application** depends only on Domain.
- **Infrastructure** implements Application interfaces.
- **API** wires everything together via dependency injection.
