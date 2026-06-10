---
description: Documentation standards
globs: docs/**/*
alwaysApply: false
---

# Documentation

Update `docs/` in same PR as code change. Search existing docs before creating duplicates.

## When

| Change | Update |
|--------|--------|
| Feature | `docs/PRD/`, `BusinessRules/` |
| API | `docs/API/openapi.yaml` |
| Schema | `docs/Database/` |
| Architecture | `docs/Architecture/adr/NNNN-title.md` |
| UI | `docs/UIUX/` |
| Deploy | `docs/DevOps/` |

## Format

kebab-case filenames · ADR: Status, Context, Decision, Consequences · link related docs

## Forbidden

Stale docs · TBD in merged PRs · secrets in docs · duplicate content
