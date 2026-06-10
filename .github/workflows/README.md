# GitHub Actions Workflows

Placeholder for CI/CD workflow definitions.

## Planned Workflows

| Workflow | Trigger | Description |
|----------|---------|-------------|
| `ci-frontend.yml` | Push, PR | Lint, build, and test React frontend |
| `ci-backend.yml` | Push, PR | Build and test .NET 10 backend |
| `ci-database.yml` | Push, PR | Validate SQL migration scripts |
| `cd-deploy.yml` | Merge to `main` | Deploy to staging/production |
| `security-scan.yml` | Scheduled, PR | Dependency and vulnerability scanning |

## Conventions

- Use environment secrets for credentials — never commit secrets to the repository.
- Pin action versions to specific SHAs or semver tags.
- Require all CI checks to pass before merging pull requests.
