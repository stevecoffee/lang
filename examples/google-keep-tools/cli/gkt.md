# gkt

Kind: leaf
Code file: `gkt.py`
Collection: `cli/`

## Purpose

Google Keep Tools — the only CLI.

## Does

Public callables (names observed at decompile):
- `build_parser`
- `dispatch`
- `main`

## Checks

- Module remains a single file (`gkt.py`) with the responsibilities above.
- Behavior matches google-keep-tools SPEC/CLI expectations for this surface when applicable.

# Agent

## Decompile
- From: `/Users/stevecoffee/projects/google-keep-tools/gkt.py`
- Lines: ~267
- Private/helpers at top level (count): 11
- Best-effort AST + docstring lift; not a line-faithful clone of implementation.
- Open: precise privileges, edge refusals, and test obligations — see product SPEC / tests in source tree.
