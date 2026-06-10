---
description: Naming conventions
alwaysApply: false
---

# Naming

Match existing names in the target module before inventing new patterns.

## .NET

`ReviewSystem.{Layer}` · PascalCase types · `I{Name}` interfaces · `{Name}Async` · `_camelCase` fields · `{Verb}{Entity}Command/Query` · file = type name

## React/TS

`PascalCase.tsx` components · `use{Name}.ts` hooks · `{name}Service.ts` · `*.types.ts` · `*.test.tsx`

## API

Plural kebab-case resources · camelCase JSON/query params

## SQL

PascalCase singular tables/columns · `V{NNN}__{desc}.sql` migrations · see `05-Database.md` for FK/IX

## Git

`feature/{desc}` branches · `type(scope): description` commits

## Forbidden

Abbreviations · Hungarian notation · inconsistent casing within a layer
