---
description: REST API design and response contracts
globs: src/backend/src/API/**/*
alwaysApply: false
---

# API

Contract: `docs/API/openapi.yaml` · extend existing controllers before creating new ones

## Routing

`/api/v1/{resource}` — plural, kebab-case · breaking changes → `/api/v2/` + ADR

## Methods

GET→200 · POST→201 · PUT/PATCH→200 · DELETE→204

## Responses

Success: DTO or `{ items, page, pageSize, totalCount }` · Error: `{ code, message, details? }`

| Status | When |
|--------|------|
| 400 | Validation · 401 | Unauth · 403 | Forbidden · 404 | Not found · 409 | Business rule · 500 | Unhandled |

## Controllers

`ISender` only · `[ProducesResponseType]` on all actions · pagination: `page`, `pageSize` · no logic, no `DbContext`, no try/catch

## Forbidden

Entities in responses · verbs in URLs · inconsistent errors · undocumented breaking changes
