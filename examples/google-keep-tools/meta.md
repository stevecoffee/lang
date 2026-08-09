# google-keep-tools

Kind: collection (product root)

## Purpose

Standalone Python toolkit for reading and writing personal Google Keep: reorg oversized lists into smaller project/category notes without data loss. CLI: `gkt`. Unofficial `gkeepapi`.

## Children (collections under `src/`)

- [backup.md](src/backup.md) + [backup/](src/backup/)
- [cli.md](src/cli.md) + [cli/](src/cli/)
- [config-paths.md](src/config-paths.md) + [config-paths/](src/config-paths/)
- [extract-plan.md](src/extract-plan.md) + [extract-plan/](src/extract-plan/)
- [keep-core.md](src/keep-core.md) + [keep-core/](src/keep-core/)
- [list-meta.md](src/list-meta.md) + [list-meta/](src/list-meta/)
- [review-ui.md](src/review-ui.md) + [review-ui/](src/review-ui/)
- [sandbox.md](src/sandbox.md) + [sandbox/](src/sandbox/)
- [scope-llm.md](src/scope-llm.md) + [scope-llm/](src/scope-llm/)

## Product facts

- Keep list roles and privilege gates
- Item ops: add, reorder, check, cross-list move
- List meta: scope, repo stamp, style
- Extract score → review → apply; backup packages; optional LLM scope scoring

# Agent

- Decompiled from `/Users/stevecoffee/projects/google-keep-tools` (production modules).
- Example root holds only `meta.md`, `README.md`, `DECOMPILE_REPORT.md` (+ `machine/` emit sink).
- All collection pairs live under `src/` (decompile-of-source layout).
- Each collection: `src/name.md` beside `src/name/` (children only inside the directory).
