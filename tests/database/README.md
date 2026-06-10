# Database Tests

Validation tests for SQL migration scripts and schema integrity.

## Scope

- Migration scripts apply cleanly on a fresh database
- Rollback scripts restore previous state
- Schema matches documented ERD
- Seed scripts are idempotent

## Tools (planned)

- tSQLt — SQL Server unit testing framework
- Custom validation scripts in CI pipeline

## Conventions

- Run database tests in CI on every PR that touches `src/database/`.
- Test against SQL Server version matching production.
