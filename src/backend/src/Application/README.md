# Application Layer

Use cases, orchestration, and application service contracts.

## Responsibilities

- Command and query handlers (CQRS)
- Data transfer objects (DTOs)
- Service and repository interfaces
- Input validation rules
- Application-level business workflows

## Subdirectories

| Directory | Purpose |
|-----------|---------|
| `Commands/` | Write operations (create, update, delete) |
| `Queries/` | Read operations (get, list, search) |
| `DTOs/` | Request and response data shapes |
| `Interfaces/` | Abstractions implemented by Infrastructure |

## Conventions

- One handler per command or query.
- Handlers depend on interfaces, not concrete Infrastructure types.
- Validate all inputs before executing business logic.
