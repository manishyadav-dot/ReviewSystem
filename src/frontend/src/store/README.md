# Store

Global application state management.

## Scope

Use global state only for data shared across multiple features:

- Authenticated user session
- Application-wide settings and preferences
- Cross-feature notifications

Feature-local state should remain within feature modules or component state.

## Conventions

- Define typed state slices with clear actions and selectors.
- Avoid storing server data long-term — prefer cache invalidation patterns.
- Document state shape changes in PR descriptions.
