---
description: AI code generation workflow and rule maintenance
alwaysApply: true
---

# AI Rules

Canonical generation rules live in `00-System-Persona.md` (always loaded). This file defines **workflow**.

## Generation Workflow

1. **Read** user request + relevant `.cursor/rules/` (auto-loaded by glob).
2. **Search** codebase — grep/semantic search for existing implementations.
3. **Reuse** — extend components, handlers, services, hooks, repos before creating new.
4. **Match** patterns in the target feature/module folder.
5. **Implement** smallest diff — only required files.
6. **Test** — update tests if behavior changed.
7. **Verify** — build/lint/test when tools available.

## Search Order

| Layer | Search First |
|-------|-------------|
| Frontend | `components/common/` → `hooks/` → `utils/` → `services/` → sibling `features/` patterns |
| Backend | `Shared/` → `Application/Interfaces/` → existing Handlers → Repositories → DTOs |
| Database | existing migrations → `schemas/` → EF configurations |
| Tests | existing `*.test.tsx` / `*Tests.cs` for same target |

## New Dependencies

Stop and ask user before adding npm or NuGet packages.

## Rule Index

| # | File | Trigger |
|---|------|---------|
| 00–02 | Persona, Overview, Architecture | Always |
| 03–06 | Frontend, Backend, Database, API | Glob |
| 07–14 | Git, Review, Testing, Security, etc. | Glob or on demand |
| 15–19 | AI-Rules, Naming, Structure, Workflow, Best Practices | On demand |

## Maintenance

One concern per file · no code examples · no duplication · update rules when patterns change + ADR
