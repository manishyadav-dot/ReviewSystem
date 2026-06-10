# Source Code

Application source organized by layer.

## Projects

| Directory | Stack | Description |
|-----------|-------|-------------|
| `frontend/` | React | Single-page application |
| `backend/` | .NET 10 + EF Core 10 | REST API and business logic |
| `database/` | SQL Server | Schemas, migrations, and scripts |

## Architecture

```
┌─────────────┐     ┌─────────────┐     ┌─────────────┐
│   Frontend  │────▶│   Backend   │────▶│   Database  │
│   (React)   │     │  (.NET 10)  │     │ (SQL Server)│
└─────────────┘     └─────────────┘     └─────────────┘
```

Each project is independently buildable and deployable. See individual README files for layer-specific conventions.
