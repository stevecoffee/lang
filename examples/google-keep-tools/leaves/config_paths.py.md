# Leaf: config_paths.py

Code file: `config_paths.py`
Source tree: google-keep-tools
Kind: leaf (compiles to this one file only)

## Purpose

Path/security helpers for config: secret files, write constrain, atomic write.

## Does

Public callables (names observed at decompile):
- `refuse_symlink_path`
- `constrain_write_path`
- `safe_write_text`

## Checks

- Module remains a single file (`config_paths.py`) with the responsibilities above.
- Behavior matches google-keep-tools SPEC/CLI expectations for this surface when applicable.

# Agent

## Decompile
- From: `/Users/stevecoffee/projects/google-keep-tools/config_paths.py`
- Lines: ~275
- Private/helpers at top level (count): 4
- Best-effort AST + docstring lift; not a line-faithful clone of implementation.
- Open: precise privileges, edge refusals, and test obligations — see product SPEC / tests in source tree.

