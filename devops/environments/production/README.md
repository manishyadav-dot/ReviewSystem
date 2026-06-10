# Production Environment

Live production environment serving end users.

## Characteristics

- Hardened security configuration
- High availability and automated backups
- Production data — handle with care
- Manual or gated approval required for all deployments

## Policies

- All changes go through staging first.
- Database migrations require a reviewed rollback plan.
- Incident response procedures documented in `docs/deployment/rollback.md`.
- No direct developer access to production data without approval.
