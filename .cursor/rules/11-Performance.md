---
description: Performance guidelines
alwaysApply: false
---

# Performance

Measure before optimizing. No premature optimization.

## Targets

API p95: reads <200ms, writes <500ms · paginate all lists · lazy-load FE routes · no N+1 queries

## Backend

`AsNoTracking()` reads · project to DTOs · `CancellationToken` everywhere · cache only with invalidation strategy

## Frontend

TanStack Query cache · `React.lazy` · debounce search · virtualize long lists

## Database

Index WHERE/JOIN/ORDER BY columns · no `SELECT *` · review plans >100ms

## Forbidden

Unbounded endpoints · N+1 · full table loads · sync I/O · cache without TTL
