# dump_list

Kind: leaf
Code file: `dump_list.py`
Collection: `src/keep-core/`

## Purpose

Dump one Keep list: items, checked state, order, nesting.

## Scope

**In scope** (belongs here):
- Read dump of one list: order, nest, checked/live views

**Out of scope** (belongs elsewhere — reject as content of this node):
- Mutations
- Backup package format

## Does

Public callables (names observed at decompile):
- `collect`
- `live_view_rows`
- `dump_list`

## Checks

- Module remains a single file (`dump_list.py`) with the responsibilities above.
- Behavior matches google-keep-tools SPEC/CLI expectations for this surface when applicable.

# Agent

## Decompile
- From: `/Users/stevecoffee/projects/google-keep-tools/dump_list.py`
- Lines: ~134
- Private/helpers at top level (count): 0
- Best-effort AST + docstring lift; not a line-faithful clone of implementation.
- Open: precise privileges, edge refusals, and test obligations — see product SPEC / tests in source tree.
