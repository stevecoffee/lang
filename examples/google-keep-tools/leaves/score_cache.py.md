# Leaf: score_cache.py

Code file: `score_cache.py`
Source tree: google-keep-tools
Kind: leaf (compiles to this one file only)

## Purpose

Score-cache filesystem, path safety, and load/save.

## Does

Public callables (names observed at decompile):
- `normalize_scope_text`
- `source_groups_fingerprint`
- `product_score_cache_root`
- `score_cache_path`
- `load_score_cache`
- `save_score_cache`

Types:
- `ScoredGroupLike` — (methods omitted)

## Checks

- Module remains a single file (`score_cache.py`) with the responsibilities above.
- Behavior matches google-keep-tools SPEC/CLI expectations for this surface when applicable.

# Agent

## Decompile
- From: `/Users/stevecoffee/projects/google-keep-tools/score_cache.py`
- Lines: ~416
- Private/helpers at top level (count): 2
- Best-effort AST + docstring lift; not a line-faithful clone of implementation.
- Open: precise privileges, edge refusals, and test obligations — see product SPEC / tests in source tree.

