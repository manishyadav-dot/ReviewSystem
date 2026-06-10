# API Contract Tests

Validate API contracts between frontend consumers and backend providers.

## Scope

- OpenAPI specification compliance
- Request/response schema validation
- Breaking change detection on API modifications

## Tools (planned)

- Pact — Consumer-driven contract testing
- OpenAPI diff tools in CI pipeline

## Conventions

- Generate OpenAPI spec from backend and validate against frontend service expectations.
- Fail CI on undocumented breaking API changes.
