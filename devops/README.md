# DevOps

Infrastructure, containerization, CI/CD pipelines, and deployment automation.

## Directory Structure

```
devops/
├── docker/              # Dockerfiles and docker-compose definitions
├── pipelines/           # CI/CD pipeline definitions
│   ├── github-actions/
│   └── azure-devops/
├── iac/                 # Infrastructure as Code
│   ├── terraform/
│   └── bicep/
├── scripts/             # Deployment and utility scripts
└── environments/        # Per-environment configuration
    ├── dev/
    ├── staging/
    └── production/
```

## Principles

- Infrastructure is version-controlled and reproducible.
- Secrets are managed via vault/secret store — never committed to the repository.
- All environments are provisioned from the same IaC templates with environment-specific parameters.
