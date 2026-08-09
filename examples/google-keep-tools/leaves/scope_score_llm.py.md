# Leaf: scope_score_llm.py

Code file: `scope_score_llm.py`
Source tree: google-keep-tools
Kind: leaf (compiles to this one file only)

## Purpose

LLM chat scope scoring: prompts, parse, single-group score, selection helpers.

## Does

Public callables (names observed at decompile):
- `has_alnum`
- `default_scope_model`
- `default_scope_threshold`
- `scope_system_prompt`
- `format_group_user_text`
- `parse_score_digit`
- `collect_scorable_groups`
- `group_item`
- `is_transport_error`
- `score_one_group`
- `refuse_on_score_errors`
- `select_by_threshold`
- `scores_histogram`
- `scores_hist_hint`

Types:
- `ScoredGroup` — `parent`

## Checks

- Module remains a single file (`scope_score_llm.py`) with the responsibilities above.
- Behavior matches google-keep-tools SPEC/CLI expectations for this surface when applicable.

# Agent

## Decompile
- From: `/Users/stevecoffee/projects/google-keep-tools/scope_score_llm.py`
- Lines: ~328
- Private/helpers at top level (count): 1
- Best-effort AST + docstring lift; not a line-faithful clone of implementation.
- Open: precise privileges, edge refusals, and test obligations — see product SPEC / tests in source tree.

