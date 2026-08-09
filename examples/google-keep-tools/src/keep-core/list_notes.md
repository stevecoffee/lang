# list_notes

Kind: leaf
Code file: `list_notes.py`
Collection: `src/keep-core/`

## Purpose

Inventory every note in Google Keep. See SPEC.md; IMPLEMENTATION.md. Read-only account inventory; does not require GKT.

## Scope

**In scope** (belongs here):
- Account inventory of notes/lists (notes list library)

**Out of scope** (belongs elsewhere — reject as content of this node):
- Single-list dump formatting (dump_list)
- Mutations

## Does

Public callables (names observed at decompile):
- `describe`
- `inventory_notes`

## Checks

- Module remains a single file (`list_notes.py`) with the responsibilities above.
- Behavior matches google-keep-tools SPEC/CLI expectations for this surface when applicable.

# Agent

## Decompile
- From: `/Users/stevecoffee/projects/google-keep-tools/list_notes.py`
- Lines: ~96
- Private/helpers at top level (count): 0
- Best-effort AST + docstring lift; not a line-faithful clone of implementation.
- Open: precise privileges, edge refusals, and test obligations — see product SPEC / tests in source tree.
