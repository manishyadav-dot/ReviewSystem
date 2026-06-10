# Backend Source

.NET 10 solution source root. See `../README.md` for architecture overview.

## Projects (planned)

| Project | Layer | Responsibility |
|---------|-------|----------------|
| `ReviewSystem.API` | API | HTTP endpoints, middleware, DI configuration |
| `ReviewSystem.Application` | Application | Commands, queries, DTOs, service interfaces |
| `ReviewSystem.Domain` | Domain | Entities, value objects, domain rules |
| `ReviewSystem.Infrastructure` | Infrastructure | EF Core 10 DbContext, repositories, external integrations |
| `ReviewSystem.Shared` | Shared | Constants, helpers, cross-cutting types |
