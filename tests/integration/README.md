# Cross-Layer Integration Tests

End-to-end tests spanning frontend, backend, and database.

## Scope

- Full request lifecycle: UI action → API call → database write → UI update
- Contract tests between frontend service layer and backend API
- Performance smoke tests for critical paths

## Subdirectories

| Directory | Purpose |
|-----------|---------|
| `api/` | API contract and consumer-driven contract tests |

## Conventions

- Run against a dedicated integration test environment.
- Use test containers or docker-compose for reproducible full-stack setup.
- Keep this suite focused — delegate layer-specific testing to `frontend/` and `backend/`.
