# Leaf: item_cli.py

Code file: `item_cli.py`
Source tree: google-keep-tools
Kind: leaf (compiles to this one file only)

## Purpose

CLI surface for ``gkt item`` — parsers and handlers.

## Does

Public callables (names observed at decompile):
- `add_item_parsers`
- `handle_item_add`
- `handle_item_reorder`
- `handle_item_check`
- `handle_item_move`

## Checks

- Module remains a single file (`item_cli.py`) with the responsibilities above.
- Behavior matches google-keep-tools SPEC/CLI expectations for this surface when applicable.

# Agent

## Decompile
- From: `/Users/stevecoffee/projects/google-keep-tools/item_cli.py`
- Lines: ~119
- Private/helpers at top level (count): 1
- Best-effort AST + docstring lift; not a line-faithful clone of implementation.
- Open: precise privileges, edge refusals, and test obligations — see product SPEC / tests in source tree.

