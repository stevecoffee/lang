# Example: google-keep-tools (decompile)

Best-effort MetaCode lift of production modules from google-keep-tools.

## Layout rule

- A **collection** is a **directory** whose children are meta files (or nested collections).
- A **leaf** is a meta file that maps to **one** code file (`Code file:` in the leaf).
- Names have **no** `C.` / `L0.` / `leaves/` prefixes; leaf files are named after the module stem (`items.md` ↔ `items.py`).
- Collection overview lives in that directory’s `meta.md`.
- Product root: [meta.md](meta.md) plus collection directories beside it.

## Collections

- [backup/](backup/)
- [cli/](cli/)
- [config-paths/](config-paths/)
- [extract-plan/](extract-plan/)
- [keep-core/](keep-core/)
- [list-meta/](list-meta/)
- [review-ui/](review-ui/)
- [sandbox/](sandbox/)
- [scope-llm/](scope-llm/)

See [DECOMPILE_REPORT.md](DECOMPILE_REPORT.md).
