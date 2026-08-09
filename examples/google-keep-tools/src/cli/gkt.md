# gkt

Kind: leaf
Code file: `gkt.py`
Collection: `src/cli/`

## Purpose

Google Keep Tools — the only CLI.

## Scope

**In scope** (belongs here):
- Root argparse, group registration, dispatch/main for gkt CLI only

**Out of scope** (belongs elsewhere — reject as content of this node):
- Library Keep operations
- Handler bodies owned by other *_cli modules beyond wiring

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
