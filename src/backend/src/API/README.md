# API Layer

ASP.NET Core Web API (.NET 10) — HTTP entry point for the application.

## Responsibilities

- REST controllers and route definitions
- Request/response serialization
- Authentication and authorization middleware
- Global exception handling and logging
- Dependency injection configuration
- Swagger/OpenAPI documentation setup

## Conventions

- Controllers are thin — delegate to Application layer handlers.
- No business logic in controllers.
- Use consistent route patterns: `api/v1/{resource}`.
- Return standardized error envelopes for all failure cases.
