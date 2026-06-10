# Frontend Integration Tests

Tests for feature modules with mocked backend services.

## Scope

- Feature workflows with multiple interacting components
- Service layer integration with mocked HTTP responses
- Store/state management interactions

## Conventions

- Mock at the service/API boundary, not inside components.
- Test realistic user interaction sequences (click, type, submit).
- Keep tests independent — no shared mutable state between tests.
