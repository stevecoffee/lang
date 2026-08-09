# review_ui

Kind: leaf
Code file: `review_ui.py`
Collection: `review-ui/`

## Purpose

Fullscreen TTY review: include/exclude scored groups before apply.

## Does

Public callables (names observed at decompile):
- `run_review`

## Checks

- Module remains a single file (`review_ui.py`) with the responsibilities above.
- Behavior matches google-keep-tools SPEC/CLI expectations for this surface when applicable.

# Agent

## Decompile
- From: `/Users/stevecoffee/projects/google-keep-tools/review_ui.py`
- Lines: ~363
- Private/helpers at top level (count): 2
- Best-effort AST + docstring lift; not a line-faithful clone of implementation.
- Open: precise privileges, edge refusals, and test obligations — see product SPEC / tests in source tree.
