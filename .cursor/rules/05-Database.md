---
description: SQL Server schema and migration conventions
globs: src/database/**/*
alwaysApply: false
---

# Database

SQL Server · scripts in `src/database/` · EF migrations in `Infrastructure/Data/Migrations/` — keep synced

## Before Writing

Search existing migrations and `schemas/` — extend, don't duplicate tables or indexes.

## Naming

Table: PascalCase singular · Column: PascalCase · PK: `{Table}Id` · FK: `FK_{Child}_{Parent}` · IX: `IX_{Table}_{Columns}`

## Migrations

`V{NNN}__{description}.sql` · sequential · never edit applied · rollback companion where feasible · idempotent (`IF NOT EXISTS`)

## Seed

Dev: sample OK · Staging: reference only · Production: no test PII

## Forbidden

Credentials in scripts · business logic in SQL · editing deployed migrations · plural/lowercase table names
