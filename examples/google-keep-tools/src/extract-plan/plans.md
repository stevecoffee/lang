# plans

Kind: leaf
Code file: `plans.py`
Collection: `src/extract-plan/`

## Purpose

Run a reviewable JSONL plan against Google Keep. See SPEC.md §5 Plans.

## Does

Public callables (names observed at decompile):
- `group_texts`
- `resolve_item`
- `apply_action`
- `run_plan`
- `load_plan`
- `run_plan_file`

Types:
- `PlanError` — (methods omitted)

## Checks

- Module remains a single file (`plans.py`) with the responsibilities above.
- Behavior matches google-keep-tools SPEC/CLI expectations for this surface when applicable.

# Agent

## Decompile
- From: `/Users/stevecoffee/projects/google-keep-tools/plans.py`
- Lines: ~565
- Private/helpers at top level (count): 4
- Best-effort AST + docstring lift; not a line-faithful clone of implementation.
- Open: precise privileges, edge refusals, and test obligations — see product SPEC / tests in source tree.
