# backup_restore

Kind: leaf
Code file: `backup_restore.py`
Collection: `src/backup/`

## Purpose

Backup group model and restore-plan generation (SPEC §6).

## Does

Public callables (names observed at decompile):
- `top_level_groups`
- `format_top_level_group_lines`
- `build_restore_plan`

Types:
- `TopLevelGroup` — (methods omitted)

## Checks

- Module remains a single file (`backup_restore.py`) with the responsibilities above.
- Behavior matches google-keep-tools SPEC/CLI expectations for this surface when applicable.

# Agent

## Decompile
- From: `/Users/stevecoffee/projects/google-keep-tools/backup_restore.py`
- Lines: ~305
- Private/helpers at top level (count): 3
- Best-effort AST + docstring lift; not a line-faithful clone of implementation.
- Open: precise privileges, edge refusals, and test obligations — see product SPEC / tests in source tree.
