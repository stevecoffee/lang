# list-meta

Kind: collection (file `src/list-meta.md` + directory `src/list-meta/` — does not compile to a code file)

## Purpose

google-keep-tools modules for **list-meta**.

## Scope

**In scope** (belongs here):
- GKT list metadata: list-scope, repo stamp, style/role stamps, snapshots of meta, reorg-rules list content
- Parse/write of meta lines under the bottom GKT parent

**Out of scope** (belongs elsewhere — reject as content of this node):
- Item body text edits unrelated to meta (items/*)
- Backup packages
- CLI only (cli/list_cli may call here but does not own meta semantics)
- LLM scoring of item relevance (scope-llm/*)

## Children

- [list_meta](list-meta/list_meta.md) ← `list_meta.py`
- [meta_parse](list-meta/meta_parse.md) ← `meta_parse.py`
- [meta_write](list-meta/meta_write.md) ← `meta_write.py`
- [meta_style](list-meta/meta_style.md) ← `meta_style.py`
- [meta_repo](list-meta/meta_repo.md) ← `meta_repo.py`
- [meta_snapshot](list-meta/meta_snapshot.md) ← `meta_snapshot.py`
- [reorg_rules](list-meta/reorg_rules.md) ← `reorg_rules.py`

# Agent

- Collection file is `src/list-meta.md` (sibling of directory `src/list-meta/`); children are only inside `list-meta/`.
- Grouping is by concern, not original source tree paths.
