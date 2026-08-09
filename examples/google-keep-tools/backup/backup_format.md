# backup_format

Kind: leaf
Code file: `backup_format.py`
Collection: `backup/`

## Purpose

Backup package format: read/write gkt-backup-v2, inventory, select (SPEC §6).

## Does

Public callables (names observed at decompile):
- `scope_from_filter_lines`
- `contained_notes`
- `build_v2_package`
- `write_backup_file`
- `package_lists`
- `list_backups`
- `select_note`

## Checks

- Module remains a single file (`backup_format.py`) with the responsibilities above.
- Behavior matches google-keep-tools SPEC/CLI expectations for this surface when applicable.

# Agent

## Decompile
- From: `/Users/stevecoffee/projects/google-keep-tools/backup_format.py`
- Lines: ~429
- Private/helpers at top level (count): 7
- Best-effort AST + docstring lift; not a line-faithful clone of implementation.
- Open: precise privileges, edge refusals, and test obligations — see product SPEC / tests in source tree.
