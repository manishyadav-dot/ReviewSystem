# DevOps Scripts

Automation scripts for deployment, provisioning, and operational tasks.

## Examples (planned)

- `deploy.sh` / `deploy.ps1` — Orchestrate full deployment
- `run-migrations.sh` — Execute pending database migrations
- `health-check.sh` — Post-deployment health validation
- `setup-local-env.ps1` — Bootstrap local development environment

## Conventions

- Scripts must be idempotent where possible.
- Support both PowerShell (Windows) and Bash (Linux/macOS) where practical.
- Document required parameters and prerequisites in script headers.
