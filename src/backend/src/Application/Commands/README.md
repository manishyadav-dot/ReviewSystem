# Commands

CQRS write-side handlers for state-changing operations.

## Naming Convention

```
{Action}{Entity}Command.cs
{Action}{Entity}CommandHandler.cs
```

Examples: `CreateReviewCommand`, `UpdateReviewCommand`, `DeleteReviewCommand`

## Guidelines

- Commands represent intent — one command per user action.
- Handlers validate input, execute domain logic, and persist changes.
- Return minimal response DTOs or operation results.
