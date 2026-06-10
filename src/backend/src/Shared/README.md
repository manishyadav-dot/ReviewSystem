# Shared

Cross-cutting utilities and constants used across backend layers.

## Examples (planned)

- `Constants.cs` — Application-wide constant values
- `Guard.cs` — Argument validation helpers
- `Result.cs` — Generic operation result wrapper
- `PaginationParams.cs` — Shared pagination request model

## Conventions

- Only place truly shared code here — prefer layer-specific locations when possible.
- No business logic or infrastructure dependencies.
- Keep this layer minimal to avoid becoming a dumping ground.
