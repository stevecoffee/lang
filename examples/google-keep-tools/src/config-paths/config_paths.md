# config_paths

Kind: leaf
Code file: `config_paths.py`
Collection: `src/config-paths/`

## Purpose

Path/security helpers for config: secret files, write constrain, atomic write.

## Scope

**In scope** (belongs here):
- Secret path allowlists, constrain_write_path, safe_write_text

**Out of scope** (belongs elsewhere — reject as content of this node):
- Settings schema
- Backup package writers (backup_io) except shared confinement ideas

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
