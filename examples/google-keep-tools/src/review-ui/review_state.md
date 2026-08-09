# review_state

Kind: leaf
Code file: `review_state.py`
Collection: `src/review-ui/`

## Purpose

Pure progressive review state machine (no curses).

## Scope

**In scope** (belongs here):
- Session state for interactive review flows

**Out of scope** (belongs elsewhere — reject as content of this node):
- Rendering only (review_ui)
- Library apply

## Does

Public callables (names observed at decompile):
- `drain_score_queue`

Types:
- `ReviewState` — `is_pending`, `is_error_unresolved`, `pending_count`, `unresolved_error_count`, `can_enter`, `score_display`, `include_mark`
- `ReviewCancelled` — (methods omitted)

## Checks

- Module remains a single file (`review_state.py`) with the responsibilities above.
- Behavior matches google-keep-tools SPEC/CLI expectations for this surface when applicable.

# Agent

## Decompile
- From: `/Users/stevecoffee/projects/google-keep-tools/review_state.py`
- Lines: ~408
- Private/helpers at top level (count): 0
- Best-effort AST + docstring lift; not a line-faithful clone of implementation.
- Open: precise privileges, edge refusals, and test obligations — see product SPEC / tests in source tree.
