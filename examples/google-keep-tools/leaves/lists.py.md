# Leaf: lists.py

Code file: `lists.py`
Source tree: google-keep-tools
Kind: leaf (compiles to this one file only)

## Purpose

Fixture inventory + list resolution helpers for google-keep-tools.

## Does

Public callables (names observed at decompile):
- `is_writable`
- `list_has_sandbox_role`
- `may_hard_delete`
- `is_purgeable`
- `resolve_sandbox_lists`
- `resolve_primary_sandbox`
- `get_writable_lists`
- `get_purgeable_lists`
- `title_of`
- `normalize_title`
- `is_keep_id`
- `parse_list_ref`
- `as_domain_error`
- `lookup_list_by_title`
- `resolve_list_by_title`
- `resolve_list_ref`
- `resolve_writable_list_by_title`
- `require_exact_title`

Types:
- `ListError` — (methods omitted)

## Checks

- Module remains a single file (`lists.py`) with the responsibilities above.
- Behavior matches google-keep-tools SPEC/CLI expectations for this surface when applicable.

# Agent

## Decompile
- From: `/Users/stevecoffee/projects/google-keep-tools/lists.py`
- Lines: ~539
- Private/helpers at top level (count): 3
- Best-effort AST + docstring lift; not a line-faithful clone of implementation.
- Open: precise privileges, edge refusals, and test obligations — see product SPEC / tests in source tree.

