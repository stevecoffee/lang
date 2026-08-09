# path_confine

Kind: leaf
Code file: `path_confine.py`
Collection: `src/config-paths/`

## Purpose

Shared filesystem path confinement and private-mode write helpers.

## Does

Public callables (names observed at decompile):
- `is_symlink`
- `collapse_macos_var_prefix`
- `path_under_dir`
- `lexical_under_dir`
- `align_path_under_root`
- `is_os_dual_prefix_symlink`
- `first_symlink_at_or_below`
- `first_symlink_below`
- `first_symlink_lexical`
- `canonical_root`
- `makedirs_no_symlink`
- `open_private_write`
- `atomic_install_private`
- `write_private_text`

## Checks

- Module remains a single file (`path_confine.py`) with the responsibilities above.
- Behavior matches google-keep-tools SPEC/CLI expectations for this surface when applicable.

# Agent

## Decompile
- From: `/Users/stevecoffee/projects/google-keep-tools/path_confine.py`
- Lines: ~431
- Private/helpers at top level (count): 3
- Best-effort AST + docstring lift; not a line-faithful clone of implementation.
- Open: precise privileges, edge refusals, and test obligations — see product SPEC / tests in source tree.
