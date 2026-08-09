# keep_auth

Kind: leaf
Code file: `keep_auth.py`
Collection: `src/keep-core/`

## Purpose

Shared login helper for google-keep-tools. See SPEC.md (Auth); IMPLEMENTATION.md.

## Does

Public callables (names observed at decompile):
- `load_credentials`
- `load_state`
- `save_state`
- `login`

## Checks

- Module remains a single file (`keep_auth.py`) with the responsibilities above.
- Behavior matches google-keep-tools SPEC/CLI expectations for this surface when applicable.

# Agent

## Decompile
- From: `/Users/stevecoffee/projects/google-keep-tools/keep_auth.py`
- Lines: ~111
- Private/helpers at top level (count): 0
- Best-effort AST + docstring lift; not a line-faithful clone of implementation.
- Open: precise privileges, edge refusals, and test obligations — see product SPEC / tests in source tree.
