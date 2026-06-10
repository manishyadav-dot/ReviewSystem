---
description: Code review standards and checklist
alwaysApply: false
---

# Code Review

## Reviewer Checks

1. Solves stated problem only — no scope creep
2. Existing code reused — not unnecessarily recreated
3. Layer boundaries respected
4. Tests updated for behavior changes
5. No new libraries without approval
6. Docs/API/schema synced if needed

## Author Checklist

- [ ] Codebase searched; existing patterns reused
- [ ] Smallest necessary diff — no unrelated file changes
- [ ] Tests added/updated
- [ ] No secrets, debug code, or unapproved dependencies
- [ ] Self-reviewed; PR template complete

## Layer Checks

| Layer | Verify |
|-------|--------|
| FE | No fetch in components; reused `common/` components; loading/error/empty states |
| BE | Thin controllers; DTOs not entities; EF in Infrastructure only |
| DB | Migration naming; rollback; no credentials |
| API | OpenAPI sync; correct status codes |

## Forbidden

Rubber-stamp · merging with failing CI · approving unnecessary new abstractions or libraries
