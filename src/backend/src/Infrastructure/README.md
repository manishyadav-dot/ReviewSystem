# Infrastructure Layer

External concerns: EF Core 10 data access, file storage, email, and third-party integrations.

## Responsibilities

- Entity Framework Core 10 `DbContext` and entity configurations
- Repository implementations
- External service adapters (email, file storage, messaging)
- EF Core migration execution via `dotnet ef database update`

## Conventions

- Implement all interfaces defined in `Application/Interfaces/`.
- Keep EF Core configurations in `Data/Configurations/`.
- No business logic — Infrastructure only handles I/O and persistence.
