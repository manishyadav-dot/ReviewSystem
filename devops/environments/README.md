# Environments

Per-environment configuration and deployment parameters.

## Environments

| Environment | Branch | Purpose |
|-------------|--------|---------|
| `dev/` | `develop` | Active development and integration testing |
| `staging/` | `release/*` | Pre-production validation and UAT |
| `production/` | `main` | Live production workloads |

## Contents (per environment)

- Application settings and connection string references (not values)
- Scaling and resource sizing parameters
- Feature flag configurations
- Deployment approval requirements

## Conventions

- Never store secrets in environment config files.
- Reference secrets by Key Vault name or environment variable key.
- Document environment-specific overrides in `docs/deployment/environments.md`.
