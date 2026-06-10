---
description: CI/CD and infrastructure
globs: "{devops/**,.github/**}"
alwaysApply: false
---

# DevOps

Paths: `devops/{docker,pipelines,iac,environments}/` · `.github/workflows/`

## Pipeline

Build → Test → Analyze → Package → Deploy

Workflows: `ci-frontend` · `ci-backend` · `ci-database` · `cd-deploy` · `security-scan`

## Environments

Dev (auto) · Staging (CI pass) · Production (manual gate)

## Rules

IaC only · pin image/action versions · secrets in store not YAML · multi-stage Docker · migration step with rollback plan · no new CI tools without approval

## Forbidden

Secrets in YAML · `:latest` in prod · skip CI · deploy without staging
