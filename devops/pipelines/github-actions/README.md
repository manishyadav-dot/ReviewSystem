# GitHub Actions Pipelines

CI/CD pipeline YAML files for GitHub Actions.

## Planned Pipelines

- `ci.yml` — Build and test all layers on PR and push
- `cd-staging.yml` — Deploy to staging on merge to `develop`
- `cd-production.yml` — Deploy to production on merge to `main`
- `database-migrate.yml` — Run pending SQL migrations

Mirror workflow definitions in `.github/workflows/` or reference them from here.
