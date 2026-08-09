# meta_snapshot

Kind: leaf
Code file: `meta_snapshot.py`
Collection: `src/list-meta/`

## Purpose

List snapshot payload/write glue and one-shot meta shape migrate.

## Scope

**In scope** (belongs here):
- List snapshot capture/rotate for meta/list state backups in-product

**Out of scope** (belongs elsewhere — reject as content of this node):
- Full gkt-backup-v2 packages (backup/*)

## Does

Public callables (names observed at decompile):
- `build_snapshot_entry`
- `build_snapshot_payload`
- `snapshot_list`
- `rotate_snapshots`
- `migrate_list_scope`

## Checks

- Module remains a single file (`meta_snapshot.py`) with the responsibilities above.
- Behavior matches google-keep-tools SPEC/CLI expectations for this surface when applicable.

# Agent

## Decompile
- From: `/Users/stevecoffee/projects/google-keep-tools/meta_snapshot.py`
- Lines: ~182
- Private/helpers at top level (count): 0
- Best-effort AST + docstring lift; not a line-faithful clone of implementation.
- Open: precise privileges, edge refusals, and test obligations — see product SPEC / tests in source tree.
