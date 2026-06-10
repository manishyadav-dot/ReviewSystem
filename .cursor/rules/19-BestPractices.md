---
description: Core engineering principles
alwaysApply: false
---

# Best Practices

## Principles

SOLID (SRP + DIP) · YAGNI · fail fast · composition over duplication · smallest change necessary

## Error Handling

Domain exceptions → middleware → HTTP (BE) · typed `ApiError` in UI (FE) · no empty catch · no stack traces to clients in prod

## Async & DI

`async/await` + `CancellationToken` · no `.Result`/`.Wait()` · inject services — no `new` for repos/services

## Dependencies

No new npm/NuGet without approval · pin versions · security scan in CI

## Maintainability

Small PRs · delete dead code · refactor only what the task requires · ADRs for significant decisions

## Forbidden

God classes · circular deps · magic values · copy-paste across features · commented-out code · TODO without issue
