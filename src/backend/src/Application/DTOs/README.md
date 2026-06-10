# DTOs

Data Transfer Objects for API request and response shapes.

## Organization

Group DTOs by resource or feature:

```
DTOs/
├── Reviews/
│   ├── CreateReviewRequest.cs
│   ├── UpdateReviewRequest.cs
│   └── ReviewResponse.cs
└── Common/
    ├── PaginatedResponse.cs
    └── ErrorResponse.cs
```

## Conventions

- DTOs are plain data containers — no business logic.
- Use separate request and response types; do not reuse domain entities.
- Keep DTOs stable; version breaking changes via API versioning.
