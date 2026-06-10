# TODO: Phase 1 - Identity & RBAC Implementation

## Backend (.NET 10) - Assigned to: Backend Team

- [ ] Add `Google.Apis.Auth` and JWT Nuget packages.
- [ ] Configure `appsettings.json` with Google Client ID and JWT Secrets.
- [ ] Create `User`, `Role`, and `UserRole` Domain Entities.
- [ ] Create EF Core Configurations and seed default roles.
- [ ] Generate initial EF Core Migration and update SQL Server database.
- [ ] Implement `GoogleAuthService` to validate tokens and generate App JWTs.
- [ ] Create `POST /api/auth/google` controller endpoint.
- [ ] Implement Role-based authorization policies (e.g., `[Authorize(Roles = "PeoplePartner")]`).

## Frontend (React) - Assigned to: Frontend Team

- [ ] Install `@react-oauth/google` and `jwt-decode`.
- [ ] Setup `VITE_GOOGLE_CLIENT_ID` in `.env`.
- [ ] Build `GoogleLoginButton` component.
- [ ] Create `authService.ts` to communicate with .NET backend.
- [ ] Implement `AuthContext` to manage token and global user state.
- [ ] Create `ProtectedRoute` component for role-based routing.
- [ ] Test login flow and role-based UI toggles (e.g., hiding the 'Executive Dashboard' from standard Employees).

## Related

| Resource | Path |
|----------|------|
| Requirements | `docs/PRD/identity-rbac.md` |
| API spec | `docs/api/authentication.md` |
| Schema | `docs/database/identity-schema.md` |
| Cursor prompts | `.cursor/prompts/identity-rbac-prompts.md` |
