# params_ui

Kind: leaf
Code file: `params_ui.py`
Collection: `review-ui/`

## Purpose

Interactive missing-params form (extract v1).

## Does

Public callables (names observed at decompile):
- `is_interactive_tty`
- `refuse_if_noninteractive`
- `build_extract_form_fields`
- `run_params_form`

Types:
- `ParamsFormCancelled` — (methods omitted)
- `FormField` — (methods omitted)
- `ListChoice` — (methods omitted)
- `ParamsFormState` — `editable_indices`, `current_field`, `move_field`, `start_edit`, `edit_insert`, `edit_backspace`

## Checks

- Module remains a single file (`params_ui.py`) with the responsibilities above.
- Behavior matches google-keep-tools SPEC/CLI expectations for this surface when applicable.

# Agent

## Decompile
- From: `/Users/stevecoffee/projects/google-keep-tools/params_ui.py`
- Lines: ~681
- Private/helpers at top level (count): 4
- Best-effort AST + docstring lift; not a line-faithful clone of implementation.
- Open: precise privileges, edge refusals, and test obligations — see product SPEC / tests in source tree.
