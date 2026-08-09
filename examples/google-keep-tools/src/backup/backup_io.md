# backup_io

Kind: leaf
Code file: `backup_io.py`
Collection: `src/backup/`

## Purpose

Backup path confinement, private-mode writes, and atomic install (SPEC §6).

## Scope

**In scope** (belongs here):
- Snapshot dir paths, basename confinement, mode-0600/atomic/gzip writers, write_plan JSONL

**Out of scope** (belongs elsewhere — reject as content of this node):
- Package JSON schema (backup_format)
- Restore planning logic
- General app config paths (config-paths) except shared patterns

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
