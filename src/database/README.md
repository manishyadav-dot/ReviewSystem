# Database (SQL Server)

SQL Server schema definitions, migrations, and operational scripts.

## Directory Structure

```
database/
├── schemas/       # Table, view, and index definitions
├── migrations/    # Versioned schema change scripts
├── scripts/       # Deployment and maintenance scripts
│   ├── deployment/
│   └── maintenance/
├── seed/          # Reference and test data scripts
└── diagrams/      # ERD and schema diagrams
```

## Conventions

- Use sequential, versioned migration files: `V001__create_reviews_table.sql`
- All scripts must be idempotent where possible.
- Document schema changes in `docs/database/` and record ADRs for significant model changes.
- Never store credentials in scripts — use environment variables or secret management.

## Naming Standards

| Object | Convention | Example |
|--------|------------|---------|
| Tables | PascalCase, singular | `Review`, `ReviewComment` |
| Columns | PascalCase | `CreatedAt`, `ReviewStatusId` |
| Primary keys | `{Table}Id` | `ReviewId` |
| Foreign keys | `FK_{Child}_{Parent}` | `FK_ReviewComment_Review` |
| Indexes | `IX_{Table}_{Columns}` | `IX_Review_StatusId` |
