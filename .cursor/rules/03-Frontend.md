---
description: React + TypeScript frontend conventions
globs: src/frontend/**/*
alwaysApply: false
---

# Frontend

React · TypeScript · Vite · React Router · TanStack Query · Vitest/RTL · Playwright

## Before Writing Code

1. Search `components/common/`, `components/layout/`, `hooks/`, `utils/` for existing solutions.
2. Reuse or compose existing components — create new only when nothing fits.
3. Follow patterns in the target `features/{name}/` module.

## Structure

`components/{common,layout}` · `features/{name}/` · `services/` · `hooks/` · `store/` · `types/` · `utils/` · `config/`

## Imports

| From | Allowed | Forbidden |
|------|---------|-----------|
| `features/` | components, hooks, services, store, types, utils, config | other features |
| `components/` | hooks, types, utils | features, services, store |
| `services/` | types, config | components, features |

## Components

Named exports · typed props · one per file · `common/` = stateless, no business logic · `layout/` = shell only

Async UI must handle: loading · error · empty

## Data

- HTTP only via `services/apiClient.ts` — types in `types/api.types.ts` match OpenAPI.
- Server state: TanStack Query. Global store: UI-only state.
- Routes in `config/routes.ts`. Lazy-load features.

## Tests

Update `tests/frontend/` when component behavior changes.

## Forbidden

`any` · default exports · `fetch` in components · cross-feature imports · new npm packages without approval · business logic in `common/` · API data in store
