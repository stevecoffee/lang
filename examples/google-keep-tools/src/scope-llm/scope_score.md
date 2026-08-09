# scope_score

Kind: leaf
Code file: `scope_score.py`
Collection: `src/scope-llm/`

## Purpose

Per-group scope scoring (approach B): one digit 0–9 per Keep group.

## Scope

**In scope** (belongs here):
- Scope-score facade for labeling items vs list-scope

**Out of scope** (belongs elsewhere — reject as content of this node):
- LLM transport (llm)
- Cache (score_cache)
- Extract apply

## Does

- Facade / re-exports or constants only (few or no public functions at module top level).

## Checks

- Module remains a single file (`scope_score.py`) with the responsibilities above.
- Behavior matches google-keep-tools SPEC/CLI expectations for this surface when applicable.

# Agent

## Decompile
- From: `/Users/stevecoffee/projects/google-keep-tools/scope_score.py`
- Lines: ~92
- Private/helpers at top level (count): 0
- Best-effort AST + docstring lift; not a line-faithful clone of implementation.
- Open: precise privileges, edge refusals, and test obligations — see product SPEC / tests in source tree.
