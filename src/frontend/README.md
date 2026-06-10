# Frontend (React)

React single-page application for ReviewSystem.

## Tech Stack

- React (with TypeScript recommended)
- State management (TBD — e.g., Redux Toolkit, Zustand, or React Context)
- HTTP client (TBD — e.g., Axios or Fetch API wrapper)
- Build tooling (TBD — e.g., Vite or Create React App)

## Directory Structure

```
frontend/
├── public/          # Static assets served as-is
└── src/
    ├── assets/      # Images, fonts, and media
    ├── components/  # Reusable UI components
    │   ├── common/  # Generic components (buttons, inputs, modals)
    │   └── layout/  # Page layout shells and navigation
    ├── config/      # App configuration and environment bindings
    ├── features/    # Feature-based modules (domain-specific UI)
    ├── hooks/       # Custom React hooks
    ├── services/    # API clients and external integrations
    ├── store/       # Global state management
    ├── types/       # TypeScript type definitions
    └── utils/       # Shared utility functions
```

## Conventions

- Organize UI by feature in `features/` — one folder per business capability.
- Keep components in `components/` generic and reusable across features.
- All API calls go through `services/` — never call endpoints directly from components.
- Co-locate feature-specific types, hooks, and tests within feature folders when practical.
