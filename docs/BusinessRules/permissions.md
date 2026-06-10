# RBAC Permission Matrix

Role-based permissions for Identity & RBAC. **API must enforce** all rules below.

Legend: ✅ Allowed · ❌ Denied · 🔶 Scoped (assigned population only)

## Authentication & Profile

| Action | Employee | Lead | Executive | PeoplePartner | Admin |
|--------|----------|------|-----------|---------------|-------|
| Sign in (Google) | ✅ | ✅ | ✅ | ✅ | ✅ |
| View own profile | ✅ | ✅ | ✅ | ✅ | ✅ |
| View others' profiles | ❌ | 🔶 | 🔶 | 🔶 | ✅ |
| Assign/revoke roles | ❌ | ❌ | ❌ | 🔶 | ✅ |
| Deactivate users | ❌ | ❌ | ❌ | ❌ | ✅ |

## Self-Review & OII

| Action | Employee | Lead | Executive | PeoplePartner | Admin |
|--------|----------|------|-----------|---------------|-------|
| Submit self-review | ✅ | ✅ | ✅ | ✅ | ❌ |
| View own OII | ✅ | ✅ | ✅ | ✅ | ❌ |
| View others' OII | ❌ | 🔶 | 🔶 | 🔶 | ❌ |

## Lead Review

| Action | Employee | Lead | Executive | PeoplePartner | Admin |
|--------|----------|------|-----------|---------------|-------|
| Submit lead review | ❌ | 🔶 | ❌ | ❌ | ❌ |
| Flag green/red behaviors | ❌ | 🔶 | ❌ | ❌ | ❌ |
| View pulse blockers (weekly) | ❌ | 🔶 | 🔶 | 🔶 | ❌ |

## Executive / Calibration

| Action | Employee | Lead | Executive | PeoplePartner | Admin |
|--------|----------|------|-----------|---------------|-------|
| Calibration actions | ❌ | ❌ | 🔶 | 🔶 | ❌ |
| Assess strategic fit | ❌ | ❌ | 🔶 | 🔶 | ❌ |
| View retention insights | ❌ | ❌ | 🔶 | 🔶 | ✅ |

## People Partner (HR)

| Action | Employee | Lead | Executive | PeoplePartner | Admin |
|--------|----------|------|-----------|---------------|-------|
| Culture fit assessment | ❌ | ❌ | ❌ | 🔶 | ❌ |
| Engagement / retention risk view | ❌ | ❌ | 🔶 | 🔶 | ✅ |
| Recommend investment actions | ❌ | ❌ | ❌ | 🔶 | ❌ |

## System & Confidential

| Action | Employee | Lead | Executive | PeoplePartner | Admin |
|--------|----------|------|-----------|---------------|-------|
| System configuration | ❌ | ❌ | ❌ | ❌ | ✅ |
| View confidential review messages | ❌ | ❌ | ❌ | ❌ | ✅ |

## JWT Role Claims

Custom JWT includes one claim per assigned role using standard `role` claim (or `ClaimTypes.Role`) with values:

`Employee` · `Lead` · `Executive` · `PeoplePartner` · `Admin`

API authorization policies map endpoints to required role(s). Multiple roles on one user = multiple claims.

## Related

- Role definitions: [identity-rbac.md](./identity-rbac.md)
- Authentication API: [../API/authentication.md](../API/authentication.md)
