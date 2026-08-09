# meta_parse

Kind: leaf
Code file: `meta_parse.py`
Collection: `list-meta/`

## Purpose

Bottom meta group parsers, guards, and metadata dump (SPEC §4).

## Does

Public callables (names observed at decompile):
- `is_meta_parent_text`
- `is_legacy_meta_parent_text`
- `is_list_scope_header`
- `is_repo_line`
- `is_legacy_filter_header`
- `is_filter_header`
- `scope_payload_from_text`
- `repo_payload_from_text`
- `rename_legacy_meta_parents`
- `find_meta_parent`
- `parse_scope`
- `parse_repo`
- `parse_filter_lines`
- `is_filter_content_item`
- `work_bottom_destination`
- `metadata_for_list`
- `dump_metadata`

## Checks

- Module remains a single file (`meta_parse.py`) with the responsibilities above.
- Behavior matches google-keep-tools SPEC/CLI expectations for this surface when applicable.

# Agent

## Decompile
- From: `/Users/stevecoffee/projects/google-keep-tools/meta_parse.py`
- Lines: ~284
- Private/helpers at top level (count): 4
- Best-effort AST + docstring lift; not a line-faithful clone of implementation.
- Open: precise privileges, edge refusals, and test obligations — see product SPEC / tests in source tree.
