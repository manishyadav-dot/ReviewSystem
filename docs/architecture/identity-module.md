# Architecture: Identity & RBAC Module

## Purpose

Authenticate users via Google Sign-In, persist identity and roles in SQL Server, issue application JWTs, and enforce RBAC on API and UI.

## Components

| Layer | Responsibility |
|-------|----------------|
| **Frontend** | Google Sign-In trigger; `authService` → API; auth context stores token + roles; conditional UI |
| **API** | `AuthController`; JWT bearer middleware; role-based authorization policies |
| **Application** | `AuthenticateWithGoogleCommand`; token validation orchestration; DTOs |
| **Domain** | `User`, `Role`, `UserRole` entities; role name constants |
| **Infrastructure** | EF Core repositories; Google token validator; JWT issuer; `ICurrentUserService` |
| **Database** | `User`, `Role`, `UserRole` tables |

## Request Flow

```
[Google Sign-In] → POST /auth/google
    → IGoogleTokenValidator.Validate(idToken)
    → IUserRepository.GetByGoogleSubjectId (or create user + Employee role)
    → IJwtTokenService.GenerateToken(userId, roles)
    → AuthResponse DTO

[Protected request] → JWT middleware
    → ICurrentUserService resolves UserId + roles
    → Authorization policy check
    → MediatR handler
```

## Security Boundaries

- Google ID token validated **only on backend** — never trust unsigned client claims for identity.
- Application JWT is the session credential for API calls.
- Role claims sourced from **database** at login time — not from Google groups (unless future ADR).
- Confidential review content: **Admin** role only (see permissions matrix).

## Integration Points

| Module | Integration |
|--------|-------------|
| Reviews | UserId on review records; Lead/Executive/PP scoped access |
| Pulse surveys | Employee submit; Lead views team blockers |
| OII | Employee views own; scoped roles view assigned population |
| Admin settings | Admin-only configuration endpoints |

## Dependencies

| Package (planned) | Purpose |
|-------------------|---------|
| `Microsoft.AspNetCore.Authentication.JwtBearer` | JWT validation |
| `Google.Apis.Auth` (or equivalent) | Google ID token validation |

New packages require explicit approval per project standards.

## Related

- ADR: [adr/0001-google-sign-in-jwt-rbac.md](./adr/0001-google-sign-in-jwt-rbac.md)
- PRD: [../PRD/identity-rbac.md](../PRD/identity-rbac.md)
- Schema: [../Database/identity-schema.md](../Database/identity-schema.md)
