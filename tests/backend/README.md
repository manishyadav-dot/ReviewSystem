# Backend Tests

Test suites for the .NET 10 backend application.

## Subdirectories

| Directory | Framework | Scope |
|-----------|-----------|-------|
| `unit/` | xUnit + Moq | Handlers, domain logic, validators |
| `integration/` | xUnit + WebApplicationFactory | API endpoints with test database |

## Conventions

- Unit tests must not require a database or external services.
- Integration tests use an in-memory or containerized SQL Server instance.
- Name test classes `{ClassUnderTest}Tests` and methods `MethodName_Scenario_ExpectedResult`.
