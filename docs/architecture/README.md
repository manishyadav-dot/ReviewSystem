# Architecture

System architecture and technical design documentation.

## Contents

- `identity-module.md` — Identity & RBAC architecture
- `adr/0001-google-sign-in-jwt-rbac.md` — Auth provider and JWT decision
- `system-overview.md` — High-level system context (planned)
- `frontend-architecture.md` — React application structure and patterns
- `backend-architecture.md` — .NET 10 clean architecture and EF Core 10 layer responsibilities
- `data-flow.md` — Request/response and data pipeline flows
- `security-architecture.md` — Authentication, authorization, and data protection
- `adr/` — Architecture Decision Records

## Principles

- Separation of concerns across frontend, API, and database layers.
- Backend (.NET 10) follows Domain → Application → Infrastructure → API layering with EF Core 10 for persistence.
- API-first design — all frontend data access via documented REST endpoints.
