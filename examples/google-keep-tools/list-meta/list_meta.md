# list_meta

Kind: leaf
Code file: `list_meta.py`
Collection: `list-meta/`

## Purpose

List metadata, list-scope, repo tag, create, snapshot. See SPEC.md §4; IMPLEMENTATION.md.

## Does

- Facade / re-exports or constants only (few or no public functions at module top level).

## Checks

- Module remains a single file (`list_meta.py`) with the responsibilities above.
- Behavior matches google-keep-tools SPEC/CLI expectations for this surface when applicable.

# Agent

## Decompile
- From: `/Users/stevecoffee/projects/google-keep-tools/list_meta.py`
- Lines: ~165
- Private/helpers at top level (count): 0
- Best-effort AST + docstring lift; not a line-faithful clone of implementation.
- Open: precise privileges, edge refusals, and test obligations — see product SPEC / tests in source tree.
