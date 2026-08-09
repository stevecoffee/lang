# meta_repo

Kind: leaf
Code file: `meta_repo.py`
Collection: `src/list-meta/`

## Purpose

Repo identity, normalize, and list healing (SPEC §4).

## Does

Public callables (names observed at decompile):
- `normalize_repo_location`
- `local_repo_candidates`
- `iter_lists_with_repo`
- `find_lists_by_repo`
- `resolve_list_by_repo`
- `resolve_list_for_local_repo`
- `resolve_project_list`

## Checks

- Module remains a single file (`meta_repo.py`) with the responsibilities above.
- Behavior matches google-keep-tools SPEC/CLI expectations for this surface when applicable.

# Agent

## Decompile
- From: `/Users/stevecoffee/projects/google-keep-tools/meta_repo.py`
- Lines: ~262
- Private/helpers at top level (count): 2
- Best-effort AST + docstring lift; not a line-faithful clone of implementation.
- Open: precise privileges, edge refusals, and test obligations — see product SPEC / tests in source tree.
