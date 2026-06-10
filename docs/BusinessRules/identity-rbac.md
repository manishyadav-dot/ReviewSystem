# Business Rules: Identity & RBAC

Source of truth for authentication identity and role definitions. Implements SmartPerform organizational roles.

## Identity Rules

1. Every authenticated user must have a unique `Email` and `GoogleSubjectId`.
2. A user may hold **multiple roles** via `UserRole` assignments.
3. New users discovered on first Google sign-in receive **Employee** only — no other roles by default.
4. Role assignment changes are performed by authorized roles (Admin; People Partner where applicable) — not self-service.
5. Deactivated users (`IsActive = false`) cannot authenticate.

## Role Definitions

### Employee

- Submit quarterly **self-reviews**.
- Answer **pulse surveys**.
- View **own OII** (Organizational Impact Index) — no access to others' OII.

### Lead

- Complete **Lead Review** evaluations for direct reports.
- Flag **green/red behaviors** on reviews.
- View **weekly pulse blockers** for direct reports only.

### Executive (Executive Leadership / Manager)

- Acts as **calibration** layer on performance outcomes.
- Assess **strategic fit** for covered population.
- View **retention insights** for organizational scope assigned to the executive.

### People Partner (HR)

- Evaluate **culture fit**, **engagement**, and **retention risk**.
- Recommend **investment actions**: Retain & Invest, Needs Intervention, and related HR actions.
- Does not replace Lead or Executive review ownership unless explicitly assigned.

### Admin (System Admin)

- Manage **system configurations** (integrations, feature flags, global settings as defined in Admin scope).
- Access **confidential messages** submitted in reviews (content marked confidential by submitters).

## Authorization Principles

- **Deny by default** — endpoints and UI actions require explicit role permission.
- **Least privilege** — roles grant minimum access for responsibilities above.
- **Scope matters** — Lead/Executive/People Partner access is limited to assigned population (direct reports, calibration cohort, HR scope). Population rules defined in respective review/survey modules.
- **Server-side enforcement** — frontend role gating is UX only; API must validate roles on every protected request.

## Role Hierarchy (informational)

Admin and People Partner are **orthogonal** to line management — not a superset of Lead/Executive. A user may be Employee + Lead, or Employee + PeoplePartner, etc.

```
Employee (base)
  ├── Lead (+ team review duties)
  ├── Executive (+ calibration duties)
  ├── PeoplePartner (+ HR assessment duties)
  └── Admin (+ system + confidential content)
```

## State Rules

| User State | Can Sign In | Notes |
|------------|-------------|-------|
| Active, roles assigned | Yes | Normal operation |
| Active, no roles | No | Data integrity error — Admin must fix |
| Inactive | No | `IsActive = false` |

## Related

- Permission matrix: [permissions.md](./permissions.md)
- API contract: [../API/authentication.md](../API/authentication.md)
- Schema: [../Database/identity-schema.md](../Database/identity-schema.md)
