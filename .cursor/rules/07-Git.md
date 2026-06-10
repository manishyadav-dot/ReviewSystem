---
description: Branching, commits, and PR workflow
alwaysApply: false
---

# Git

## Branches

`main` (prod) · `develop` (integration) · `feature/` · `bugfix/` · `hotfix/` · `release/`

## Commits

`{type}({scope}): {description}` — types: feat, fix, refactor, docs, test, chore, ci · one logical change · no secrets

## PRs

Target `develop` (features) or `main` (hotfix) · use PR template · CI must pass · smallest diff — no unrelated files

## Forbidden

Direct push to `main`/`develop` · force push `main` · build artifacts · mixed unrelated changes
