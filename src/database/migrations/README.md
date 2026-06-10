# Migrations

Versioned SQL scripts for incremental schema changes.

## Naming Convention

```
V{NNN}__{description}.sql
```

Examples:
- `V001__initial_schema.sql`
- `V002__add_review_status_column.sql`
- `V003__create_review_comments_table.sql`

## Guidelines

- Migrations run in order — never modify a migration that has been applied to any environment.
- Include a rollback script companion where feasible: `V002__add_review_status_column.rollback.sql`
- Test migrations against a copy of production data before applying to staging.
- Track applied migrations in a `SchemaVersions` table.
