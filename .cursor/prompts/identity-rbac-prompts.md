# Cursor AI Prompts for Identity & RBAC

Use with `Identity_RBAC_Requirements.md` in this folder. Follow `.cursor/rules/` before generating code.

---

## Backend Prompt 1: Domain Entities & EF Core

> Read the `Identity_RBAC_Requirements.md` file. I need to implement the database schema for our Identity system using .NET 10 Clean Architecture. Please generate the Domain entities for `User`, `Role`, and `UserRole` (many-to-many relationship). Ensure strongly-typed IDs are used. Then, generate the EF Core `IEntityTypeConfiguration` classes for these entities to seed the default roles: Employee, Lead, Executive, PeoplePartner, Admin.

**Scope**

- `ReviewSystem.Domain` — entities, typed IDs, no framework references
- `ReviewSystem.Infrastructure/Data/Configurations/` — fluent API configs
- Seed roles in EF configuration or migration — not on domain entities
- Tables: `User`, `Role`, `UserRole` per `docs/database/identity-schema.md`

**Do not**

- Add EF attributes on domain entities
- Create Login/Dashboard pages
- Refactor unrelated backend files

---

## Backend Prompt 2: Auth Service & Google Validation

> Generate the `IAuthService` and its implementation. It needs a method `LoginWithGoogleAsync(string googleIdToken)`. This method should:
> 1. Validate the Google token using `Google.Apis.Auth`.
> 2. Query the EF Core `DbContext` to find the user by their Google Email.
> 3. If the user doesn't exist, create them and assign the default 'Employee' role.
> 4. Generate and return a custom JWT that includes the user's roles as Claims.
> Use C# 14 syntax and ensure asynchronous database calls.

**Scope**

- `IAuthService` in `ReviewSystem.Application/Interfaces/`
- Implementation in `ReviewSystem.Infrastructure/Services/`
- `AuthController` — `POST /api/v1/auth/google` dispatches to service (or thin controller → service)
- JWT config via `appsettings` + User Secrets — no hardcoded keys
- Also match by `GoogleSubjectId` when email lookup fails (see requirements)

**Returns**

- DTO with `accessToken`, `expiresIn`, `user` (id, email, fullName, roles)

**Do not**

- Put business logic in controller
- Inject `DbContext` into controller — service/repository only
- Skip `CancellationToken` on async methods

---

## Frontend Prompt 3: React Auth Context & Route Guards

> Read the `Identity_RBAC_Requirements.md` file. Generate a React `AuthContext.tsx` that stores the user's custom JWT and decodes it to expose their roles. Then, create a `ProtectedRoute.tsx` wrapper component that takes an `allowedRoles` array prop. If the logged-in user does not have the required role, redirect them to an 'Unauthorized' page.

**Scope**

- `src/frontend/src/features/identity/` — `AuthContext.tsx`, hooks (`useAuth`)
- `src/frontend/src/components/layout/ProtectedRoute.tsx`
- `src/frontend/src/features/identity/UnauthorizedPage.tsx` — minimal unauthorized view (not a Dashboard)
- `src/frontend/src/services/authService.ts` — `loginWithGoogle(idToken)` calls `POST /api/v1/auth/google`
- Route paths in `config/routes.ts`

**Behavior**

- Context exposes: `user`, `roles`, `isAuthenticated`, `login`, `logout`
- Decode JWT client-side for roles **for UI only** — API enforces auth
- `ProtectedRoute` checks `allowedRoles` against context roles

**Do not**

- Call `fetch` directly from context — use `services/`
- Build Login/Dashboard modules unless explicitly requested
- Store tokens in code or commit secrets

---

## Prompt Order

1. Backend Prompt 1 (entities + EF) → run EF migration
2. Backend Prompt 2 (auth service + API)
3. Frontend Prompt 3 (context + guards) — after API contract is stable
