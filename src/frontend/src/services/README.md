# Services

API client layer for backend communication.

## Structure (planned)

```
services/
├── apiClient.ts       # Base HTTP client with auth headers and interceptors
├── endpoints.ts       # Centralized API endpoint constants
└── {resource}Service.ts  # Per-resource API methods
```

## Conventions

- All HTTP calls to the backend go through this layer.
- Handle authentication token injection in `apiClient.ts`.
- Map API responses to typed objects defined in `types/`.
- Never import services directly into `components/common/` — use hooks or feature services instead.
