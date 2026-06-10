# Config

Application configuration and environment variable bindings.

## Contents (planned)

- `env.ts` — Typed environment variable access
- `constants.ts` — Application-wide constants (pagination defaults, timeouts)
- `routes.ts` — Frontend route path definitions

## Conventions

- Never hardcode environment-specific values — use environment variables.
- Provide sensible defaults for local development.
- Document all required environment variables in `docs/onboarding/`.
