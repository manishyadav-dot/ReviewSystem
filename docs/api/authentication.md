# API: Authentication

Google Sign-In exchange and custom JWT usage for ReviewSystem.

Base path: `/api/v1/auth`

## Flow

```
React (Google Sign-In)
    → POST /api/v1/auth/google { idToken }
    → Backend validates Google JWT
    → EF Core: User + UserRole lookup (or create User + Employee)
    → Backend issues custom JWT (UserId + role claims)
    → Frontend stores token; attaches to subsequent requests
```

## Endpoints

### POST `/api/v1/auth/google`

Exchange Google ID token for application JWT.

**Auth:** Public (no application JWT required)

**Request body:**

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `idToken` | string | Yes | Google ID token from client Sign-In |

**Success (200):**

| Field | Type | Description |
|-------|------|-------------|
| `accessToken` | string | Application JWT |
| `expiresIn` | number | Token lifetime in seconds |
| `user` | object | User profile summary |
| `user.id` | guid | Internal user ID |
| `user.email` | string | User email |
| `user.fullName` | string | Display name |
| `user.roles` | string[] | Assigned role names |

**Errors:**

| Status | When |
|--------|------|
| 400 | Missing or invalid `idToken` |
| 401 | Google token validation failed |
| 403 | User exists but `IsActive = false` |
| 500 | Server error |

### GET `/api/v1/auth/me`

Return current user profile and roles from application JWT.

**Auth:** Bearer JWT required

**Success (200):** Same `user` shape as google response (no token).

**Errors:** 401 unauthorized · 404 user not found

## Custom JWT

| Claim | Description |
|-------|-------------|
| `sub` | User ID (Guid) |
| `email` | User email |
| `role` | One claim per role (Employee, Lead, Executive, PeoplePartner, Admin) |

**Transport:** `Authorization: Bearer {accessToken}`

**Validation:** ASP.NET Core JWT bearer middleware on protected endpoints.

## Google Token Validation

- Validate issuer, audience, signature, and expiry against Google client configuration.
- Extract `sub` (Google subject ID), `email`, and `name` from validated token.
- Map `sub` → `User.GoogleSubjectId`; never trust client-supplied user ID.

## Configuration (reference)

| Setting | Description |
|---------|-------------|
| `Google:ClientId` | Google OAuth client ID |
| `Jwt:Issuer` | Application token issuer |
| `Jwt:Audience` | Application token audience |
| `Jwt:SigningKey` | Symmetric key or key reference (secret store) |
| `Jwt:ExpirationMinutes` | Access token lifetime |

Secrets must not be committed — use User Secrets / Key Vault.

## Frontend Contract

- Store token per security policy (session storage or memory + refresh strategy as defined in security standards).
- Attach Bearer token in `services/apiClient.ts` for all protected calls.
- Drive UI visibility from `user.roles` — API remains authoritative.

## Related

- PRD: [../PRD/identity-rbac.md](../PRD/identity-rbac.md)
- Permissions: [../BusinessRules/permissions.md](../BusinessRules/permissions.md)
- Schema: [../Database/identity-schema.md](../Database/identity-schema.md)
