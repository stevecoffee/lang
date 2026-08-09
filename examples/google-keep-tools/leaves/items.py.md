# Leaf: items.py

Code file: `items.py`
Source tree: google-keep-tools
Kind: leaf (compiles to this one file only)

## Purpose

Item manipulation primitives for Google Keep lists. See SPEC.md; IMPLEMENTATION.md.

## Does

Public callables (names observed at decompile):
- `resolve_default_list_id`
- `get_target_list`
- `show`
- `ordered_items`
- `find_item`
- `siblings_of`
- `Before`
- `After`
- `compute_positions_after_move`
- `append_subitem`
- `child_order`
- `destination_from`
- `cmd_move`
- `cmd_check`
- `cmd_add`
- `run_xmove`
- `run_item_command`

Types:
- `RefusalError` — (methods omitted)
- `MoveError` — (methods omitted)
- `XmoveError` — (methods omitted)

## Checks

- Module remains a single file (`items.py`) with the responsibilities above.
- Behavior matches google-keep-tools SPEC/CLI expectations for this surface when applicable.

# Agent

## Decompile
- From: `/Users/stevecoffee/projects/google-keep-tools/items.py`
- Lines: ~649
- Private/helpers at top level (count): 0
- Best-effort AST + docstring lift; not a line-faithful clone of implementation.
- Open: precise privileges, edge refusals, and test obligations — see product SPEC / tests in source tree.

