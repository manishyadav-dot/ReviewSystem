# Identity & RBAC Requirements

Reference document for Cursor AI prompts. Full specs in `docs/`.

## Overview

Google Sign-In authentication with role-based access stored in SQL Server via EF Core 10. Backend issues custom JWT with role claims. Frontend gates UI by role.

## Roles (seed required)

| Name | Responsibilities |
|------|------------------|
| `Employee` | Self-reviews, pulse surveys, own OII — **default for new users** |
| `Lead` | Lead reviews, green/red flags, team pulse blockers |
| `Executive` | Calibration, strategic fit, retention insights |
| `PeoplePartner` | Culture fit, engagement, retention risk, investment actions |
| `Admin` | System config, confidential review messages |

## Authentication Flow

1. React triggers Google Sign-In → sends Google ID token to API.
2. Backend validates Google token.
3. EF Core loads `User` + `UserRole` by `GoogleSubjectId` (primary) or `Email`.
4. New user → create `User` + assign `Employee` role.
5. Backend returns custom JWT (`UserId` + `role` claims).
6. Frontend stores JWT; `AuthContext` exposes roles; `ProtectedRoute` gates routes.

## Domain Entities

| Entity | Key Fields |
|--------|------------|
| `User` | Id, Email, FullName, GoogleSubjectId, CreatedAt, IsActive |
| `Role` | Id, Name |
| `UserRole` | Id, UserId, RoleId, AssignedAt |

Use **strongly-typed IDs** (e.g. record structs or typed wrappers for `UserId`, `RoleId`).

## Database Tables

`User` · `Role` · `UserRole` (many-to-many). PascalCase. See `docs/database/identity-schema.md`.

## API Endpoints

| Method | Path | Auth |
|--------|------|------|
| POST | `/api/v1/auth/google` | Public — body: `{ idToken }` |
| GET | `/api/v1/auth/me` | Bearer JWT |

See `docs/api/authentication.md`.

## JWT Claims

- `sub` — User ID
- `email` — User email
- `role` — one claim per assigned role

## Project Paths

| Layer | Path |
|-------|------|
| Domain | `src/backend/src/ReviewSystem.Domain/` |
| Application | `src/backend/src/ReviewSystem.Application/` |
| Infrastructure | `src/backend/src/ReviewSystem.Infrastructure/` |
| API | `src/backend/src/ReviewSystem.API/` |
| EF Configurations | `Infrastructure/Data/Configurations/` |
| EF Migrations | `Infrastructure/Data/Migrations/` |
| Frontend features | `src/frontend/src/features/identity/` |
| Frontend services | `src/frontend/src/services/` |
| Route guards | `src/frontend/src/components/layout/` |

## Architecture Constraints

- Clean Architecture: Domain has no EF/ASP.NET dependencies.
- EF fluent config only — no attributes on domain entities.
- Follow `.cursor/rules/04-Backend.md` and `03-Frontend.md`.
- Search codebase before creating new files; smallest change necessary.
- No new NuGet/npm packages without approval (`Google.Apis.Auth`, JWT packages are approved for this module).

## Related Docs

| Doc | Path |
|-----|------|
| PRD | `docs/PRD/identity-rbac.md` |
| Business rules | `docs/BusinessRules/identity-rbac.md` |
| Permissions | `docs/BusinessRules/permissions.md` |
| API | `docs/api/authentication.md` |
| Schema | `docs/database/identity-schema.md` |
| Architecture | `docs/architecture/identity-module.md` |
| ADR | `docs/architecture/adr/0001-google-sign-in-jwt-rbac.md` |
