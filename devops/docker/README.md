# Docker

Container definitions for local development and deployment.

## Planned Files

| File | Purpose |
|------|---------|
| `Dockerfile.frontend` | Multi-stage build for React SPA |
| `Dockerfile.backend` | .NET 10 API container |
| `docker-compose.yml` | Full local stack (frontend, backend, SQL Server) |
| `docker-compose.override.yml` | Local developer overrides (gitignored) |

## Conventions

- Use multi-stage builds to minimize image size.
- Run containers as non-root users in production images.
- Pin base image versions for reproducibility.
