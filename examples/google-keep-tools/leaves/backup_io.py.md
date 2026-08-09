# Leaf: backup_io.py

Code file: `backup_io.py`
Source tree: google-keep-tools
Kind: leaf (compiles to this one file only)

## Purpose

Backup path confinement, private-mode writes, and atomic install (SPEC §6).

## Does

Public callables (names observed at decompile):
- `write_plan`

## Checks

- Module remains a single file (`backup_io.py`) with the responsibilities above.
- Behavior matches google-keep-tools SPEC/CLI expectations for this surface when applicable.

# Agent

## Decompile
- From: `/Users/stevecoffee/projects/google-keep-tools/backup_io.py`
- Lines: ~227
- Private/helpers at top level (count): 7
- Best-effort AST + docstring lift; not a line-faithful clone of implementation.
- Open: precise privileges, edge refusals, and test obligations — see product SPEC / tests in source tree.

