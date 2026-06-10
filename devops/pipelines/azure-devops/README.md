# Azure DevOps Pipelines

CI/CD pipeline YAML files for Azure DevOps.

## Planned Pipelines

- `azure-pipelines-ci.yml` — Continuous integration (build + test)
- `azure-pipelines-cd.yml` — Continuous deployment to Azure resources
- `azure-pipelines-db.yml` — Database migration pipeline

## Conventions

- Use variable groups for environment-specific settings.
- Link service connections for Azure resource deployment.
- Require approval gates for production deployments.
