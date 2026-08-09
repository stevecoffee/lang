# google-keep-tools

Kind: collection (product root — this example’s top directory)

## Purpose

Standalone Python toolkit for reading and writing personal Google Keep: reorg oversized lists into smaller project/category notes without data loss. CLI: `gkt`. Unofficial `gkeepapi`.

## Children (collections)

- [backup.md](backup.md) + [backup/](backup/)
- [cli.md](cli.md) + [cli/](cli/)
- [config-paths.md](config-paths.md) + [config-paths/](config-paths/)
- [extract-plan.md](extract-plan.md) + [extract-plan/](extract-plan/)
- [keep-core.md](keep-core.md) + [keep-core/](keep-core/)
- [list-meta.md](list-meta.md) + [list-meta/](list-meta/)
- [review-ui.md](review-ui.md) + [review-ui/](review-ui/)
- [sandbox.md](sandbox.md) + [sandbox/](sandbox/)
- [scope-llm.md](scope-llm.md) + [scope-llm/](scope-llm/)


## Product facts

- Keep list roles and privilege gates
- Item ops: add, reorder, check, cross-list move
- List meta: scope, repo stamp, style
- Extract score → review → apply; backup packages; optional LLM scope scoring

# Agent

- Each collection is a **pair**: `name.md` (collection meta) beside `name/` (leaf children only).
- No collection `meta.md` inside the child directory (avoids name clash with a leaf like `backup.md`).

- Decompiled from `/Users/stevecoffee/projects/google-keep-tools` (production modules).
- Layout: each collection is a **directory** of child meta files; no `C.` / `L0.` / `leaves/` prefixes.
- Does not mirror original source tree paths.
