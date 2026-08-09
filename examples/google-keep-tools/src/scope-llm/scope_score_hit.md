# scope_score_hit

Kind: leaf
Code file: `scope_score_hit.py`
Collection: `src/scope-llm/`

## Purpose

Score-cache hit resolve and merge into progressive seed rows.

## Does

Public callables (names observed at decompile):
- `identity_key`
- `cache_row_ok`
- `resolve_cache_hits`
- `prepare_progressive_scoring`

## Checks

- Module remains a single file (`scope_score_hit.py`) with the responsibilities above.
- Behavior matches google-keep-tools SPEC/CLI expectations for this surface when applicable.

# Agent

## Decompile
- From: `/Users/stevecoffee/projects/google-keep-tools/scope_score_hit.py`
- Lines: ~212
- Private/helpers at top level (count): 0
- Best-effort AST + docstring lift; not a line-faithful clone of implementation.
- Open: precise privileges, edge refusals, and test obligations — see product SPEC / tests in source tree.
