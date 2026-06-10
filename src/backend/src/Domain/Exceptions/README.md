# Domain Exceptions

Business rule violation exceptions thrown from the Domain layer.

## Examples (planned)

- `EntityNotFoundException` — Requested entity does not exist
- `BusinessRuleViolationException` — Operation violates a domain invariant
- `DuplicateEntityException` — Unique constraint violation at domain level

## Conventions

- Domain exceptions carry meaningful messages for logging and API error mapping.
- Map to appropriate HTTP status codes in the API exception middleware.
- Do not use generic `Exception` for business rule failures.
