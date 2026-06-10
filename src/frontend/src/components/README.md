# Components

Reusable, presentation-focused UI components shared across features.

## Subdirectories

| Directory | Purpose |
|-----------|---------|
| `common/` | Generic UI primitives — buttons, inputs, tables, modals, loaders |
| `layout/` | Application shell — header, sidebar, footer, page containers |

## Conventions

- Components should be stateless where possible; lift state to features or hooks.
- Accept data and callbacks via props — avoid fetching data inside shared components.
- One component per file; co-locate a `.test.tsx` in `tests/frontend/`.
- Use TypeScript props interfaces for all public component APIs.
