---
description: Auth, secrets, and data protection
alwaysApply: false
---

# Security

## Secrets

Never commit credentials. Local: User Secrets/`.env`. Deployed: Key Vault. Rotate on exposure.

## Auth

API middleware enforces auth. Permissions in handlers via `ICurrentUserService`. Document auth per endpoint in OpenAPI.

## Data

HTTPS in non-local · EF Core parameterized queries only · validate all input · no PII/secrets in logs · least-privilege DB accounts

## Dependencies

Vulnerability scan in CI. **New packages require explicit approval.**

## Forbidden

Hardcoded secrets · frontend-only auth · production stack traces · `AllowAnonymous` without approval · SQL string interpolation
