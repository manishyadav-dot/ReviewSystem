# Tests

All test projects and suites for the ReviewSystem application.

## Structure

| Directory | Scope |
|-----------|-------|
| `frontend/` | React component, hook, and E2E tests |
| `backend/` | .NET 10 unit and integration tests |
| `database/` | SQL script and migration validation tests |
| `integration/` | Cross-layer API and end-to-end integration tests |

## Testing Pyramid

```
        ┌─────────┐
        │   E2E   │  Few, high-value user journey tests
        ├─────────┤
        │ Integr. │  API and service integration tests
        ├─────────┤
        │  Unit   │  Many fast, isolated unit tests
        └─────────┘
```

## Conventions

- Tests mirror the source structure they validate.
- Name test files `{ClassUnderTest}.test.{ext}` or `{ClassUnderTest}Tests.cs`.
- All tests must pass in CI before merging.
- Target meaningful coverage of business logic — avoid testing framework internals.
