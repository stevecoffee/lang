# clear_sandbox

Kind: leaf
Code file: `clear_sandbox.py`
Collection: `sandbox/`

## Purpose

Bulk check-off of the primary hard-delete sandbox. See SPEC.md §3.

## Does

Public callables (names observed at decompile):
- `clear_primary_sandbox`

## Checks

- Module remains a single file (`clear_sandbox.py`) with the responsibilities above.
- Behavior matches google-keep-tools SPEC/CLI expectations for this surface when applicable.

# Agent

## Decompile
- From: `/Users/stevecoffee/projects/google-keep-tools/clear_sandbox.py`
- Lines: ~70
- Private/helpers at top level (count): 0
- Best-effort AST + docstring lift; not a line-faithful clone of implementation.
- Open: precise privileges, edge refusals, and test obligations — see product SPEC / tests in source tree.
