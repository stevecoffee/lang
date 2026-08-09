# meta_write

Kind: leaf
Code file: `meta_write.py`
Collection: `src/list-meta/`

## Purpose

List property writers: colour, pin, list-scope, and repo tags (SPEC §4; IMPLEMENTATION.md).

## Does

Public callables (names observed at decompile):
- `parse_color`
- `set_color`
- `set_pinned`
- `set_scope`
- `clear_scope`
- `set_repo`
- `clear_repo`

## Checks

- Module remains a single file (`meta_write.py`) with the responsibilities above.
- Behavior matches google-keep-tools SPEC/CLI expectations for this surface when applicable.

# Agent

## Decompile
- From: `/Users/stevecoffee/projects/google-keep-tools/meta_write.py`
- Lines: ~476
- Private/helpers at top level (count): 17
- Best-effort AST + docstring lift; not a line-faithful clone of implementation.
- Open: precise privileges, edge refusals, and test obligations — see product SPEC / tests in source tree.
