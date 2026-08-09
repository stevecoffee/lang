# extract_prepare

Kind: leaf
Code file: `extract_prepare.py`
Collection: `src/extract-plan/`

## Purpose

Extract prepare layer: resolve source/dest, analyze CLI args, missing-params form.

## Scope

**In scope** (belongs here):
- Resolve source/dest, analyze extract params, missing-param handling

**Out of scope** (belongs elsewhere — reject as content of this node):
- LLM scoring (scope-llm)
- Plan apply (extract_apply/plans)

## Does

Public callables (names observed at decompile):
- `resolve_scope_text`
- `try_default_master_source`
- `resolve_source_ref_error`
- `collect_labeled_list_choices`
- `analyze_extract_params`
- `validate_resolved_extract_values`
- `prepare_extract_args`

## Checks

- Module remains a single file (`extract_prepare.py`) with the responsibilities above.
- Behavior matches google-keep-tools SPEC/CLI expectations for this surface when applicable.

# Agent

## Decompile
- From: `/Users/stevecoffee/projects/google-keep-tools/extract_prepare.py`
- Lines: ~516
- Private/helpers at top level (count): 3
- Best-effort AST + docstring lift; not a line-faithful clone of implementation.
- Open: precise privileges, edge refusals, and test obligations — see product SPEC / tests in source tree.
