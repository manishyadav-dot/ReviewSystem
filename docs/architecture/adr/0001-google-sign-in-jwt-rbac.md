# 0001. Google Sign-In with Custom JWT and Database RBAC

Date: 2026-06-10
Status: Accepted

## Context

ReviewSystem requires enterprise authentication aligned with SmartPerform roles (Employee, Lead, Executive, People Partner, Admin). Users already have Google workspace accounts. The system must enforce fine-grained RBAC stored internally, not delegated to Google group membership alone.

## Decision

1. **Authentication provider:** Google Sign-In on the frontend; backend validates Google ID tokens.
2. **Identity store:** SQL Server tables `User`, `Role`, `UserRole` via EF Core 10.
3. **Session credential:** Custom JWT issued by the API containing `UserId` and `role` claims mapped from database assignments.
4. **Default provisioning:** New users receive **Employee** role automatically on first successful sign-in.
5. **Authorization:** ASP.NET Core JWT bearer + role policies on API; React context for UI gating (non-authoritative).

## Alternatives Considered

| Alternative | Rejected Because |
|-------------|------------------|
| Google groups → roles mapping | Org roles don't map 1:1 to Google groups; SmartPerform roles are application-specific |
| Session cookies only | SPA + API split favors Bearer JWT; aligns with mobile/API clients later |
| Azure AD / Entra only | Product spec requires Google Sign-In for current rollout |

## Consequences

**Positive**

- Full control of RBAC in application database.
- Clear separation: Google proves identity; app proves authorization.
- Aligns with clean architecture (validators and handlers in Application layer).

**Negative**

- Must operate JWT signing key lifecycle (rotation, Key Vault).
- Role changes require re-login or token refresh strategy to pick up new roles.
- Google token validation dependency on Google APIs or library.

## Follow-up

- Define token refresh strategy if role changes must apply without re-login (future ADR).
- Document Google OAuth client setup in `docs/Onboarding/`.
