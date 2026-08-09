# scope_score_run

Kind: leaf
Code file: `scope_score_run.py`
Collection: `src/scope-llm/`

## Purpose

Progressive / batch scope-score runners (queue worker + score_groups).

## Scope

**In scope** (belongs here):
- Run loop orchestrating scope scoring over items

**Out of scope** (belongs elsewhere — reject as content of this node):
- CLI
- Plan apply

## Does

Public callables (names observed at decompile):
- `sequential_score_to_queue`
- `score_groups`

## Checks

- Module remains a single file (`scope_score_run.py`) with the responsibilities above.
- Behavior matches google-keep-tools SPEC/CLI expectations for this surface when applicable.

# Agent

## Decompile
- From: `/Users/stevecoffee/projects/google-keep-tools/scope_score_run.py`
- Lines: ~210
- Private/helpers at top level (count): 0
- Best-effort AST + docstring lift; not a line-faithful clone of implementation.
- Open: precise privileges, edge refusals, and test obligations — see product SPEC / tests in source tree.
