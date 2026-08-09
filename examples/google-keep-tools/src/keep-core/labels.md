# labels

Kind: leaf
Code file: `labels.py`
Collection: `src/keep-core/`

## Purpose

Labels for google-keep-tools. See SPEC.md §3–§4 (GKT labels).

## Scope

**In scope** (belongs here):
- GKT role labels attach/ensure, privilege gates for writes

**Out of scope** (belongs elsewhere — reject as content of this node):
- Item text edits
- Backup
- LLM

## Does

Public callables (names observed at decompile):
- `label_cache_path`
- `label_names_on`
- `role_labels_on`
- `list_is_managed`
- `list_has_gkt`
- `list_level`
- `level_at_least`
- `require_level`
- `is_valid_sandbox`
- `normalize_role_label`
- `role_label_name`
- `lists_with_label`
- `resolve_one_list_by_role`
- `ensure_role_label`
- `find_existing_label`
- `ensure_gkt_label`
- `stamp_gkt_on_new_list`
- `attach_label`
- `detach_label`
- `run_label_command`

## Checks

- Module remains a single file (`labels.py`) with the responsibilities above.
- Behavior matches google-keep-tools SPEC/CLI expectations for this surface when applicable.

# Agent

## Decompile
- From: `/Users/stevecoffee/projects/google-keep-tools/labels.py`
- Lines: ~600
- Private/helpers at top level (count): 8
- Best-effort AST + docstring lift; not a line-faithful clone of implementation.
- Open: precise privileges, edge refusals, and test obligations — see product SPEC / tests in source tree.
