# Frontend Unit Tests

Fast, isolated tests for components, hooks, and utility functions.

## Coverage Targets

- All utility functions in `src/frontend/src/utils/`
- Shared components in `src/frontend/src/components/common/`
- Custom hooks in `src/frontend/src/hooks/`

## Conventions

- One describe block per component or function.
- Use `@testing-library/react` for component rendering and queries.
- Avoid testing implementation details — test behavior and user-visible output.
