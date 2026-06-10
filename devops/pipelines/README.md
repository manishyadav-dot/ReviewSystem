# Pipelines

CI/CD pipeline definitions for automated build, test, and deploy.

## Platforms

| Directory | Platform |
|-----------|----------|
| `github-actions/` | GitHub Actions workflows |
| `azure-devops/` | Azure DevOps pipeline YAML |

Choose the platform matching your organization's tooling. Pipeline stages are equivalent across both.

## Standard Pipeline Stages

1. **Build** — Compile frontend and backend
2. **Test** — Run unit, integration, and database tests
3. **Analyze** — Code quality and security scanning
4. **Package** — Build Docker images or deployment artifacts
5. **Deploy** — Push to target environment
