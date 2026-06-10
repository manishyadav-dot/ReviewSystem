# Interfaces

Application-layer abstractions implemented by the Infrastructure layer.

## Examples (planned)

- `IReviewRepository` — Data access for review entities
- `IUnitOfWork` — Transaction boundary management
- `IEmailService` — External email notification service
- `ICurrentUserService` — Authenticated user context

## Conventions

- Define interfaces here; implement in `Infrastructure/`.
- Keep interfaces focused — prefer small, role-specific interfaces.
- Register implementations via DI in the API layer startup.
