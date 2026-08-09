# google-keep-tools

Kind: collection (product root — this example’s top directory)

## Purpose

Standalone Python toolkit for reading and writing personal Google Keep: reorg oversized lists into smaller project/category notes without data loss. CLI: `gkt`. Unofficial `gkeepapi`.

## Children (collections = directories)

- [backup/](backup/) — see [backup/meta.md](backup/meta.md)
- [cli/](cli/) — see [cli/meta.md](cli/meta.md)
- [config-paths/](config-paths/) — see [config-paths/meta.md](config-paths/meta.md)
- [extract-plan/](extract-plan/) — see [extract-plan/meta.md](extract-plan/meta.md)
- [keep-core/](keep-core/) — see [keep-core/meta.md](keep-core/meta.md)
- [list-meta/](list-meta/) — see [list-meta/meta.md](list-meta/meta.md)
- [review-ui/](review-ui/) — see [review-ui/meta.md](review-ui/meta.md)
- [sandbox/](sandbox/) — see [sandbox/meta.md](sandbox/meta.md)
- [scope-llm/](scope-llm/) — see [scope-llm/meta.md](scope-llm/meta.md)

## Product facts

- Keep list roles and privilege gates
- Item ops: add, reorder, check, cross-list move
- List meta: scope, repo stamp, style
- Extract score → review → apply; backup packages; optional LLM scope scoring

# Agent

- Decompiled from `/Users/stevecoffee/projects/google-keep-tools` (production modules).
- Layout: each collection is a **directory** of child meta files; no `C.` / `L0.` / `leaves/` prefixes.
- Does not mirror original source tree paths.
