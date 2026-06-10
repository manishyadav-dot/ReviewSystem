# Queries

CQRS read-side handlers for data retrieval operations.

## Naming Convention

```
Get{Entity}Query.cs
Get{Entity}ListQuery.cs
{Entity}QueryHandler.cs
```

Examples: `GetReviewByIdQuery`, `GetReviewListQuery`

## Guidelines

- Queries are read-only — no side effects.
- Return DTOs, never domain entities directly to the API layer.
- Support filtering, sorting, and pagination via query parameters.
