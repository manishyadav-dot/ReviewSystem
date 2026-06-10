# Schemas

Full schema definitions for tables, views, indexes, and constraints.

## Structure (planned)

```
schemas/
├── tables/        # CREATE TABLE scripts
├── views/         # CREATE VIEW scripts
├── indexes/       # Index definitions
└── constraints/   # Foreign key and check constraints
```

Use this directory for reference schema snapshots. Incremental changes go in `migrations/`.
