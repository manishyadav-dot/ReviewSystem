# Backend Unit Tests

Isolated tests for Application handlers, Domain logic, and validators.

## Coverage Targets

- All command and query handlers
- Domain entity business rule enforcement
- FluentValidation rules
- Shared utility functions

## Conventions

- Mock all external dependencies (repositories, services).
- Use Arrange-Act-Assert pattern.
- One assertion concept per test where practical.
