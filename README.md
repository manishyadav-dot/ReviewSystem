# ReviewSystem

Enterprise AI-assisted software development platform.

## Overview

This repository contains the full stack for the ReviewSystem application:

| Layer | Technology | Location |
|-------|------------|----------|
| Frontend | React | `src/frontend/` |
| Backend | .NET 10 + EF Core 10 | `src/backend/` |
| Database | SQL Server | `src/database/` |
| Documentation | Markdown | `docs/` |
| AI Rules | Cursor rules | `.cursor/rules/` |
| DevOps | Docker, IaC, Pipelines | `devops/` |
| Testing | Unit, Integration, E2E | `tests/` |

## Repository Structure

```
ReviewSystem/
├── .cursor/rules/       # AI assistant rules and conventions
├── .github/             # GitHub workflows, issue/PR templates
├── config/              # Shared configuration references
├── devops/              # CI/CD, containers, infrastructure
├── docs/                # Architecture, API, and developer docs
├── src/
│   ├── frontend/        # React application
│   ├── backend/         # .NET 10 API and services
│   └── database/        # SQL Server schemas and scripts
└── tests/               # All test projects and suites
```

## Getting Started

1. Review `docs/onboarding/` for environment setup instructions.
2. Read `docs/Standards/` for coding standards and workflows.
3. Configure your IDE with rules from `.cursor/rules/`.
4. Follow the branching strategy described in `docs/Standards/git-workflow.md`.

## Contributing

See `docs/Standards/` for contribution guidelines and pull request expectations.
