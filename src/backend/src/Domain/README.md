# Domain Layer

Core business entities, rules, and domain-specific exceptions.

## Responsibilities

- Entity definitions with business invariants
- Domain enums and value objects
- Domain-specific exceptions
- Pure domain logic with no infrastructure dependencies

## Conventions

- No references to Application, Infrastructure, or API layers.
- No ORM attributes on entities — configure mappings in Infrastructure.
- Enforce business rules within entity methods or domain services.
