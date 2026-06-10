# Frontend Source

Application source root. See `../README.md` for the full directory map.

## Entry Points (planned)

- `main.tsx` — Application bootstrap
- `App.tsx` — Root component with routing
- `index.css` — Global styles

## Module Organization

| Directory | Responsibility |
|-----------|----------------|
| `components/` | Shared, presentation-focused UI building blocks |
| `features/` | Self-contained feature modules with UI, hooks, and local state |
| `services/` | Backend API communication layer |
| `store/` | Application-wide state |
| `hooks/` | Reusable React hooks |
| `types/` | Shared TypeScript interfaces and types |
| `utils/` | Pure utility functions with no side effects |
| `config/` | Environment and runtime configuration |
| `assets/` | Bundled static assets (images, fonts) |
