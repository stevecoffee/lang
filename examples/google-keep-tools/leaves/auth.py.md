# Leaf: auth.py

Code file: `auth.py`
Source tree: google-keep-tools
Kind: leaf (compiles to this one file only)

## Purpose

Verify Google Keep authentication. CLI: ``gkt auth``.

## Does

Public callables (names observed at decompile):
- `run_auth`

## Checks

- Module remains a single file (`auth.py`) with the responsibilities above.
- Behavior matches google-keep-tools SPEC/CLI expectations for this surface when applicable.

# Agent

## Decompile
- From: `/Users/stevecoffee/projects/google-keep-tools/auth.py`
- Lines: ~24
- Private/helpers at top level (count): 0
- Best-effort AST + docstring lift; not a line-faithful clone of implementation.
- Open: precise privileges, edge refusals, and test obligations — see product SPEC / tests in source tree.

