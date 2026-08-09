# Leaf: purge_sandbox.py

Code file: `purge_sandbox.py`
Source tree: google-keep-tools
Kind: leaf (compiles to this one file only)

## Purpose

Hard-delete checked items from valid sandboxes only. See SPEC.md §3.

## Does

Public callables (names observed at decompile):
- `purge_list`
- `purge_sandboxes`

## Checks

- Module remains a single file (`purge_sandbox.py`) with the responsibilities above.
- Behavior matches google-keep-tools SPEC/CLI expectations for this surface when applicable.

# Agent

## Decompile
- From: `/Users/stevecoffee/projects/google-keep-tools/purge_sandbox.py`
- Lines: ~109
- Private/helpers at top level (count): 0
- Best-effort AST + docstring lift; not a line-faithful clone of implementation.
- Open: precise privileges, edge refusals, and test obligations — see product SPEC / tests in source tree.

