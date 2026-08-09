# Example: google-keep-tools (decompile)

Best-effort MetaCode lift of production modules from google-keep-tools.

## Layout rule

A **collection** is two siblings in the same folder:

```text
backup.md          ← collection meta (constraints / child list)
backup/            ← directory of children only (leaves)
  backup.md        ← leaf ↔ backup.py
  backup_format.md
  …
```

- Collection file sits **one level up**, not inside the self-named directory.
- Leaves live **only** in the directory; named by module stem (`items.md` ↔ `items.py`).
- No `C.` / `L0.` / inner collection `meta.md`.
- Product root: [meta.md](meta.md) plus collection pairs beside it.

## Collections

- [backup.md](backup.md) / [backup/](backup/)
- [cli.md](cli.md) / [cli/](cli/)
- [config-paths.md](config-paths.md) / [config-paths/](config-paths/)
- [extract-plan.md](extract-plan.md) / [extract-plan/](extract-plan/)
- [keep-core.md](keep-core.md) / [keep-core/](keep-core/)
- [list-meta.md](list-meta.md) / [list-meta/](list-meta/)
- [review-ui.md](review-ui.md) / [review-ui/](review-ui/)
- [sandbox.md](sandbox.md) / [sandbox/](sandbox/)
- [scope-llm.md](scope-llm.md) / [scope-llm/](scope-llm/)

See [DECOMPILE_REPORT.md](DECOMPILE_REPORT.md).
