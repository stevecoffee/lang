# meta_style

Kind: leaf
Code file: `meta_style.py`
Collection: `src/list-meta/`

## Purpose

Kind style constants and list create/style helpers (SPEC §4; IMPLEMENTATION.md).

## Does

Public callables (names observed at decompile):
- `apply_kind_style`
- `create_empty_list`
- `refuse_wrong_kind_title_prefix`
- `normalize_kind_title`
- `create_kind_list`

## Checks

- Module remains a single file (`meta_style.py`) with the responsibilities above.
- Behavior matches google-keep-tools SPEC/CLI expectations for this surface when applicable.

# Agent

## Decompile
- From: `/Users/stevecoffee/projects/google-keep-tools/meta_style.py`
- Lines: ~230
- Private/helpers at top level (count): 1
- Best-effort AST + docstring lift; not a line-faithful clone of implementation.
- Open: precise privileges, edge refusals, and test obligations — see product SPEC / tests in source tree.
