# config

Kind: leaf
Code file: `config.py`
Collection: `src/config-paths/`

## Purpose

GKT settings: config-file first, with optional env compatibility.

## Scope

**In scope** (belongs here):
- Public config facade: precedence docstring surface re-exports

**Out of scope** (belongs elsewhere — reject as content of this node):
- settings/paths/llm implementation modules

## Does

- Facade / re-exports or constants only (few or no public functions at module top level).

## Checks

- Module remains a single file (`config.py`) with the responsibilities above.
- Behavior matches google-keep-tools SPEC/CLI expectations for this surface when applicable.

# Agent

## Decompile
- From: `/Users/stevecoffee/projects/google-keep-tools/config.py`
- Lines: ~171
- Private/helpers at top level (count): 0
- Best-effort AST + docstring lift; not a line-faithful clone of implementation.
- Open: precise privileges, edge refusals, and test obligations — see product SPEC / tests in source tree.
