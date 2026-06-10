# Frontend Tests

Test suites for the React frontend application.

## Subdirectories

| Directory | Tool (recommended) | Scope |
|-----------|-------------------|-------|
| `unit/` | Vitest + React Testing Library | Components, hooks, utilities |
| `integration/` | Vitest | Feature modules with mocked API |
| `e2e/` | Playwright or Cypress | Full user journeys in a browser |

## Conventions

- Co-locate unit tests near source or mirror structure here.
- Mock API calls in unit/integration tests — use real API only in E2E.
- E2E tests run against a deployed or locally started full stack.
