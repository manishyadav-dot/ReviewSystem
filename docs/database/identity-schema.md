# Database: Identity & RBAC Schema

SQL Server tables for users, roles, and assignments. Mapped by EF Core 10 in `ReviewSystem.Infrastructure`.

## Entity Relationship

```
User ──────< UserRole >────── Role
```

- `User` ↔ `Role`: many-to-many via `UserRole`
- New users: one `UserRole` row linking to seeded `Employee` role

## Table: User

| Column | Type | Constraints | Description |
|--------|------|-------------|-------------|
| `UserId` | `uniqueidentifier` | PK | Internal user identifier |
| `Email` | `nvarchar(256)` | NOT NULL, UNIQUE | Login email from Google |
| `FullName` | `nvarchar(200)` | NOT NULL | Display name |
| `GoogleSubjectId` | `nvarchar(128)` | NOT NULL, UNIQUE | Google `sub` claim |
| `CreatedAt` | `datetime2` | NOT NULL | UTC creation timestamp |
| `IsActive` | `bit` | NOT NULL, DEFAULT 1 | Account active flag |

**Indexes:** `IX_User_Email` · `IX_User_GoogleSubjectId`

## Table: Role

| Column | Type | Constraints | Description |
|--------|------|-------------|-------------|
| `RoleId` | `int` | PK | Role identifier |
| `Name` | `nvarchar(50)` | NOT NULL, UNIQUE | System role name |

**Seed data (required):**

| Name | Description |
|------|-------------|
| `Employee` | Default role for new users |
| `Lead` | Line manager / lead reviewer |
| `Executive` | Executive leadership / calibration |
| `PeoplePartner` | HR / people partner |
| `Admin` | System administrator |

## Table: UserRole

| Column | Type | Constraints | Description |
|--------|------|-------------|-------------|
| `UserRoleId` | `uniqueidentifier` | PK | Assignment identifier |
| `UserId` | `uniqueidentifier` | FK → User, NOT NULL | User reference |
| `RoleId` | `int` | FK → Role, NOT NULL | Role reference |
| `AssignedAt` | `datetime2` | NOT NULL | UTC assignment timestamp |

**Constraints:**

- `FK_UserRole_User` → `User.UserId`
- `FK_UserRole_Role` → `Role.RoleId`
- `UQ_UserRole_UserId_RoleId` — prevent duplicate assignments

**Indexes:** `IX_UserRole_UserId` · `IX_UserRole_RoleId`

## EF Core Mapping Notes

- Fluent configuration in `Infrastructure/Data/Configurations/` — no attributes on domain entities.
- Domain entities: `User`, `Role`, `UserRole` in `ReviewSystem.Domain`.
- Migrations: `Infrastructure/Data/Migrations/` (primary).
- Optional SQL mirror: `src/database/migrations/V001__identity_tables.sql` — keep in sync.

## Provisioning Rules

1. On first Google sign-in: insert `User`, insert `UserRole` for `Employee`.
2. Role changes: Admin (or authorized HR) inserts/deletes `UserRole` rows — never hard-delete `User` for audit; use `IsActive`.

## Related

- PRD: [../PRD/identity-rbac.md](../PRD/identity-rbac.md)
- API: [../API/authentication.md](../API/authentication.md)
- Naming: project rule `05-Database.md` (PascalCase tables)
