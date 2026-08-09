# extract

Kind: leaf
Code file: `extract.py`
Collection: `src/extract-plan/`

## Purpose

Score (B) → optional TTY review → apply create_list + moves.

## Scope

**In scope** (belongs here):
- Extract facade: score→review→apply product path entry

**Out of scope** (belongs elsewhere — reject as content of this node):
- prepare/score/apply implementations (siblings)
- CLI

## Does

- Facade / re-exports or constants only (few or no public functions at module top level).

## Checks

- Module remains a single file (`extract.py`) with the responsibilities above.
- Behavior matches google-keep-tools SPEC/CLI expectations for this surface when applicable.

# Agent

## Decompile
- From: `/Users/stevecoffee/projects/google-keep-tools/extract.py`
- Lines: ~77
- Private/helpers at top level (count): 0
- Best-effort AST + docstring lift; not a line-faithful clone of implementation.
- Open: precise privileges, edge refusals, and test obligations — see product SPEC / tests in source tree.
