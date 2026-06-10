# Entities

Domain entity classes representing core business objects.

## Guidelines

- Each entity encapsulates its own business invariants.
- Use factory methods or constructors to enforce valid state at creation.
- Avoid anemic models — include behavior, not just properties.
- No database or framework attributes — keep entities persistence-ignorant.
