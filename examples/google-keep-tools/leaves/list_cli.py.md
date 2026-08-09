# Leaf: list_cli.py

Code file: `list_cli.py`
Source tree: google-keep-tools
Kind: leaf (compiles to this one file only)

## Purpose

CLI surface for ``gkt list`` — parsers, handlers, and presentation.

## Does

Public callables (names observed at decompile):
- `add_list_parsers`
- `handle_list_show`
- `handle_list_meta`
- `handle_list_create`
- `handle_list_style`
- `handle_list_color`
- `handle_list_pin`
- `handle_list_unpin`
- `handle_list_set_scope`
- `handle_list_clear_scope`
- `handle_list_set_repo`
- `handle_list_clear_repo`
- `handle_list_find_by_repo`
- `handle_list_snapshot`
- `handle_list_migrate_scope`
- `handle_list_rotate`

## Checks

- Module remains a single file (`list_cli.py`) with the responsibilities above.
- Behavior matches google-keep-tools SPEC/CLI expectations for this surface when applicable.

# Agent

## Decompile
- From: `/Users/stevecoffee/projects/google-keep-tools/list_cli.py`
- Lines: ~332
- Private/helpers at top level (count): 2
- Best-effort AST + docstring lift; not a line-faithful clone of implementation.
- Open: precise privileges, edge refusals, and test obligations — see product SPEC / tests in source tree.

