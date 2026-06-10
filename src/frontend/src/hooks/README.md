# Hooks

Custom React hooks for shared logic across components and features.

## Examples (planned)

- `useApi` — Generic data fetching with loading/error states
- `useDebounce` — Debounced value for search inputs
- `useLocalStorage` — Persist state to browser local storage
- `usePagination` — Pagination state management

## Conventions

- Prefix all hooks with `use`.
- Keep hooks focused on a single concern.
- Feature-specific hooks belong in `features/{name}/hooks/` unless broadly reusable.
