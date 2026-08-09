# plan_cli

Kind: leaf
Code file: `plan_cli.py`
Collection: `cli/`

## Purpose

CLI surface for ``gkt plan`` — parsers and handlers.

## Does

Public callables (names observed at decompile):
- `add_plan_parsers`
- `handle_plan_extract`
- `handle_plan_show`
- `handle_plan_dry_run`
- `handle_plan_apply`

## Checks

- Module remains a single file (`plan_cli.py`) with the responsibilities above.
- Behavior matches google-keep-tools SPEC/CLI expectations for this surface when applicable.

# Agent

## Decompile
- From: `/Users/stevecoffee/projects/google-keep-tools/plan_cli.py`
- Lines: ~212
- Private/helpers at top level (count): 1
- Best-effort AST + docstring lift; not a line-faithful clone of implementation.
- Open: precise privileges, edge refusals, and test obligations — see product SPEC / tests in source tree.
