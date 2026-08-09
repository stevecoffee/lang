# backup_cli

Kind: leaf
Code file: `backup_cli.py`
Collection: `src/cli/`

## Purpose

CLI surface for ``gkt backup`` — parsers, handlers, and presentation.

## Does

Public callables (names observed at decompile):
- `add_backup_diff_args`
- `add_backup_parsers`
- `handle_backup_list`
- `handle_backup_show`
- `handle_backup_package`
- `handle_backup_diff`

## Checks

- Module remains a single file (`backup_cli.py`) with the responsibilities above.
- Behavior matches google-keep-tools SPEC/CLI expectations for this surface when applicable.

# Agent

## Decompile
- From: `/Users/stevecoffee/projects/google-keep-tools/backup_cli.py`
- Lines: ~209
- Private/helpers at top level (count): 0
- Best-effort AST + docstring lift; not a line-faithful clone of implementation.
- Open: precise privileges, edge refusals, and test obligations — see product SPEC / tests in source tree.
