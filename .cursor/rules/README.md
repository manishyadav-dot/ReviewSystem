# Cursor Rules (00–19)

Token-optimized. No code examples. Details in `docs/`.

## AI Generation Rules (in `00`, always on)

Search codebase · reuse existing code · follow feature patterns · composition over duplication · smallest change · no unrelated refactors · no new libraries without approval · update tests on behavior change

## Load Strategy

| Trigger | Files |
|---------|-------|
| Always | 00, 01, 02, 15 |
| Glob | 03–06, 09, 12–14 |
| On demand | 07–08, 10–11, 16–19 |

| # | File | Glob |
|---|------|------|
| 03 | Frontend | `src/frontend/**/*` |
| 04 | Backend | `src/backend/**/*` |
| 05 | Database | `src/database/**/*` |
| 06 | API | `src/backend/src/API/**/*` |
| 09 | Testing | `tests/**/*` |
| 12 | Logging | `src/**/*` |
| 13 | Documentation | `docs/**/*` |
| 14 | DevOps | `devops/**`, `.github/**` |
