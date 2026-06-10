# Seed Data

Reference and development seed data scripts.

## Usage

| Environment | Seed Strategy |
|-------------|---------------|
| Development | Full seed with sample data for local testing |
| Staging | Minimal reference data (lookup tables, roles) |
| Production | Reference data only — no test/sample records |

## Conventions

- Seed scripts must be rerunnable (use `MERGE` or `IF NOT EXISTS` patterns).
- Never seed production with personally identifiable test data.
- Keep seed data in sync with schema migrations.
