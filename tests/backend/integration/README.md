# Backend Integration Tests

API endpoint tests with a real (test) database and full DI container.

## Scope

- HTTP request/response for all API endpoints
- Database persistence and retrieval
- Authentication and authorization enforcement
- Error response format validation

## Conventions

- Use `WebApplicationFactory` for in-process API hosting.
- Reset database state between tests (transaction rollback or fresh seed).
- Test both success and failure paths for each endpoint.
