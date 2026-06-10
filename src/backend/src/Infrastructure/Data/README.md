# Data Access

Entity Framework Core 10 database context, configurations, and repositories.

## Structure (planned)

```
Data/
├── ApplicationDbContext.cs
├── Configurations/     # EF Core 10 fluent API entity configurations
├── Repositories/       # Repository implementations
└── Migrations/         # EF Core 10 code-first migrations
```

## Conventions

- Use fluent API configurations — no data annotations on domain entities.
- Repository methods return domain entities; Application layer maps to DTOs.
- Coordinate transactions through `IUnitOfWork`.
- Target `Microsoft.EntityFrameworkCore.SqlServer` provider for .NET 10.
