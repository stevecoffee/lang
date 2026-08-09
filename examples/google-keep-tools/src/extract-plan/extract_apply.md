# extract_apply

Kind: leaf
Code file: `extract_apply.py`
Collection: `src/extract-plan/`

## Purpose

Extract apply layer: plan lines + create_list/moves via ``plans.run_plan``.

## Does

Public callables (names observed at decompile):
- `build_plan_lines`
- `extract_groups`

## Checks

- Module remains a single file (`extract_apply.py`) with the responsibilities above.
- Behavior matches google-keep-tools SPEC/CLI expectations for this surface when applicable.

# Agent

## Decompile
- From: `/Users/stevecoffee/projects/google-keep-tools/extract_apply.py`
- Lines: ~185
- Private/helpers at top level (count): 0
- Best-effort AST + docstring lift; not a line-faithful clone of implementation.
- Open: precise privileges, edge refusals, and test obligations — see product SPEC / tests in source tree.
