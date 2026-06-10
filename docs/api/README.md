# API

REST API specifications and contracts for the ReviewSystem backend.

## Contents

- `authentication.md` — Google Sign-In, JWT exchange, `/auth` endpoints
- `openapi.yaml` — OpenAPI 3.x specification (planned)
- `error-handling.md` — Standard error response format and status codes
- `versioning.md` — API versioning strategy
- `endpoints/` — Per-resource endpoint documentation

## Conventions

- Base URL pattern: `/api/v1/{resource}`
- Document all breaking changes in release notes and Architecture ADRs.
- Keep the OpenAPI spec in sync with the implemented backend.
