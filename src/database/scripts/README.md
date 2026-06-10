# Scripts

Operational SQL scripts for deployment and database maintenance.

## Subdirectories

| Directory | Purpose |
|-----------|---------|
| `deployment/` | Environment setup, initial provisioning |
| `maintenance/` | Index rebuilds, statistics updates, cleanup jobs |

## Conventions

- All scripts must be reviewed before running in production.
- Include a header comment with purpose, author, and date.
- Log script execution in deployment runbooks (`docs/deployment/`).
