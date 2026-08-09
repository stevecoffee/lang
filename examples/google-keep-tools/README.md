# Example: google-keep-tools (decompile)

Best-effort MetaCode lift of production modules from google-keep-tools.

## Root (only these + emit)

| File | Role |
|------|------|
| [meta.md](meta.md) | Product root collection |
| [README.md](README.md) | This file |
| [DECOMPILE_REPORT.md](DECOMPILE_REPORT.md) | Exercise notes |
| [machine/](machine/) | Compile emit sink (empty) |

## Meta body: `src/`

Decompilation of **source** lives under **`src/`**. Other top-down examples may use different folder names; for this exercise `src/` is intentional.

```text
src/
  backup.md          ← collection
  backup/            ← leaves only
    backup.md        ← leaf ↔ backup.py
    backup_format.md
    …
  cli.md
  cli/
  …
```

- Collection = `name.md` **beside** `name/` (not inside it).
- Leaf names = module stem (`items.md` ↔ `items.py`).
- Does not mirror the original repo tree; grouping is by concern.

## Collections

- [src/backup.md](src/backup.md) / [src/backup/](src/backup/)
- [src/cli.md](src/cli.md) / [src/cli/](src/cli/)
- [src/config-paths.md](src/config-paths.md) / [src/config-paths/](src/config-paths/)
- [src/extract-plan.md](src/extract-plan.md) / [src/extract-plan/](src/extract-plan/)
- [src/keep-core.md](src/keep-core.md) / [src/keep-core/](src/keep-core/)
- [src/list-meta.md](src/list-meta.md) / [src/list-meta/](src/list-meta/)
- [src/review-ui.md](src/review-ui.md) / [src/review-ui/](src/review-ui/)
- [src/sandbox.md](src/sandbox.md) / [src/sandbox/](src/sandbox/)
- [src/scope-llm.md](src/scope-llm.md) / [src/scope-llm/](src/scope-llm/)
