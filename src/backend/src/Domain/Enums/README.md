# Enums

Domain enumeration types for fixed sets of business values.

## Examples (planned)

- `ReviewStatus` — Draft, Submitted, Approved, Rejected
- `UserRole` — Admin, Reviewer, Contributor

## Conventions

- Define enums in the Domain layer — they represent business concepts.
- Map to database values in Infrastructure EF Core 10 configurations.
- Expose human-readable labels via extension methods or lookup tables.
