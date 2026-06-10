# Frontend E2E Tests

End-to-end browser tests for critical user journeys.

## Scope

- Core user workflows across the full application stack
- Cross-browser compatibility (Chromium minimum)
- Responsive layout validation at key breakpoints

## Conventions

- Run against a dedicated test environment with seeded data.
- Use page object pattern to keep selectors maintainable.
- Keep E2E suite lean — reserve for high-value journeys only.
- Capture screenshots and traces on failure for debugging.
