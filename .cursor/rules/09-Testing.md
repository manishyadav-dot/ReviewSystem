---
description: Test strategy, structure, and naming
globs: tests/**/*
alwaysApply: false
---

# Testing

**Rule: behavior change = test change in the same PR.**

## Pyramid

Unit (many) → Integration (some) → E2E (few)

## Locations

| Layer | Path | Tool |
|-------|------|------|
| FE unit/integration | `tests/frontend/{unit,integration}/` | Vitest + RTL |
| FE E2E | `tests/frontend/e2e/` | Playwright |
| BE unit | `tests/backend/unit/` | xUnit + Moq |
| BE integration | `tests/backend/integration/` | WebApplicationFactory |
| DB | `tests/database/` | Script validation |
| Cross-layer | `tests/integration/` | API contract |

## Coverage Focus

Domain rules · handler logic · HTTP status/shape · component user-visible behavior · service HTTP boundary

## Conventions

`Method_Scenario_ExpectedResult` (BE) · `{Name}.test.tsx` (FE) · Arrange → Act → Assert · independent tests · reset DB between integration runs

## Before Adding Tests

Search `tests/` for existing test files for the component/handler — extend, don't duplicate.

## Forbidden

Skipping tests on behavior changes · testing internals · flaky/skipped tests · E2E for every CRUD · ordered test dependencies
