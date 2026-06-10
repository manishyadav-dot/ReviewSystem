# GitHub Configuration

This directory contains GitHub-specific automation and templates.

## Contents

| Path | Purpose |
|------|---------|
| `workflows/` | CI/CD pipeline definitions (build, test, deploy) |
| `ISSUE_TEMPLATE/` | Standardized issue reporting templates |
| `PULL_REQUEST_TEMPLATE.md` | Pull request checklist and description template |

## Workflows

Workflows are organized by concern:

- **CI** — Build and test on every push and pull request
- **CD** — Deploy to target environments on merge to protected branches
- **Security** — Dependency scanning and code analysis

See `workflows/README.md` for workflow details.
