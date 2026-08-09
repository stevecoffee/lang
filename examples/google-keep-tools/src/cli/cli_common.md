# cli_common

Kind: leaf
Code file: `cli_common.py`
Collection: `src/cli/`

## Purpose

Shared CLI helpers for gkt group modules (list / item / plan / shell / backup).

## Does

Public callables (names observed at decompile):
- `resolve_list_id`

## Checks

- Module remains a single file (`cli_common.py`) with the responsibilities above.
- Behavior matches google-keep-tools SPEC/CLI expectations for this surface when applicable.

# Agent

## Decompile
- From: `/Users/stevecoffee/projects/google-keep-tools/cli_common.py`
- Lines: ~58
- Private/helpers at top level (count): 3
- Best-effort AST + docstring lift; not a line-faithful clone of implementation.
- Open: precise privileges, edge refusals, and test obligations — see product SPEC / tests in source tree.
