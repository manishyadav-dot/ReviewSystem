# Features

Feature-based modules organized by business capability.

## Structure

Each feature folder is self-contained:

```
features/
└── {feature-name}/
    ├── components/    # Feature-specific UI components
    ├── hooks/         # Feature-specific hooks
    ├── services/      # Feature-specific API calls (if not in global services/)
    ├── types/         # Feature-specific types
    └── index.ts       # Public exports for the feature
```

## Guidelines

- One folder per business feature or user workflow.
- Features should not import from other features directly — use shared `components/`, `services/`, or `store/` instead.
- Keep feature boundaries aligned with backend API resource groupings where practical.
