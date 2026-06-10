# PRD: Identity & RBAC Module

## Overview

The Identity & RBAC module authenticates users via **Google Sign-In** and maps each user to one or more organizational roles stored in SQL Server via **EF Core 10**. Authorization is enforced on the API using role claims embedded in a custom JWT issued by the backend.

## Goals

- Single sign-on through Google for all users.
- Strict role-based access aligned with SmartPerform organizational roles.
- New users auto-provisioned with default **Employee** role.
- Frontend renders capabilities based on assigned roles.

## Out of Scope (this module)

- User self-registration with email/password.
- Full user administration UI (role assignment UI may be a separate feature).
- OAuth providers other than Google (future ADR required).

## User Roles

| Role | System Name | Default |
|------|-------------|---------|
| Employee | `Employee` | Yes (new users) |
| Lead | `Lead` | No |
| Executive Leadership (Manager) | `Executive` | No |
| People Partner (HR) | `PeoplePartner` | No |
| System Admin | `Admin` | No |

## Role Responsibilities (summary)

| Role | Key Capabilities |
|------|------------------|
| **Employee** | Submit quarterly self-reviews; answer pulse surveys; view own OII (Organizational Impact Index) |
| **Lead** | Lead reviews for direct reports; flag green/red behaviors; view weekly pulse blockers for team |
| **Executive** | Calibration layer; assess strategic fit; view retention insights |
| **People Partner** | Evaluate culture fit, engagement, retention risk; recommend investment actions (Retain & Invest, Needs Intervention) |
| **Admin** | System configuration; view confidential messages submitted in reviews |

Detailed rules: [BusinessRules/identity-rbac.md](../BusinessRules/identity-rbac.md)

## Authentication Flow

1. React app triggers Google Sign-In.
2. Frontend sends Google JWT to .NET 10 Web API.
3. Backend validates the Google token.
4. EF Core queries `User` and `UserRole`; existing user loads roles; new user created with `Employee` role.
5. Backend issues custom JWT with `UserId` and role claims.
6. Frontend stores token; UI gated by role.

Full specification: [API/authentication.md](../API/authentication.md)

## Data Model

Entities: `User`, `Role`, `UserRole` (many-to-many).

Schema detail: [Database/identity-schema.md](../Database/identity-schema.md)

## Architecture

Module design: [Architecture/identity-module.md](../Architecture/identity-module.md)

ADR: [Architecture/adr/0001-google-sign-in-jwt-rbac.md](../Architecture/adr/0001-google-sign-in-jwt-rbac.md)

## Acceptance Criteria

- [ ] User can sign in with Google and receive a valid application JWT.
- [ ] New Google user is created with `Employee` role only.
- [ ] Returning user receives JWT reflecting current DB roles.
- [ ] API rejects requests without valid JWT (except public auth endpoints).
- [ ] API enforces role requirements per endpoint.
- [ ] Frontend shows/hides features based on role claims.
- [ ] Roles seeded in database: Employee, Lead, Executive, PeoplePartner, Admin.

## Related Documents

| Document | Purpose |
|----------|---------|
| `docs/BusinessRules/identity-rbac.md` | Role rules and permissions |
| `docs/BusinessRules/permissions.md` | RBAC permission matrix |
| `docs/API/authentication.md` | Endpoints and token contract |
| `docs/Database/identity-schema.md` | Tables and constraints |
