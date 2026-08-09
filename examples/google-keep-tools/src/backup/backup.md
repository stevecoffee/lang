# backup

Kind: leaf
Code file: `backup.py`
Collection: `src/backup/`

## Purpose

Backup inventory, show, and restore-plan generators (SPEC §6).

## Scope

**In scope** (belongs here):
- Public facade re-exports for backup inventory/package/restore-plan APIs

**Out of scope** (belongs elsewhere — reject as content of this node):
- Format/IO/restore implementation (sibling modules)
- CLI
- Applying plans

## Does

- Facade / re-exports or constants only (few or no public functions at module top level).

## Checks

- Module remains a single file (`backup.py`) with the responsibilities above.
- Behavior matches google-keep-tools SPEC/CLI expectations for this surface when applicable.

# Agent

## Decompile
- From: `/Users/stevecoffee/projects/google-keep-tools/backup.py`
- Lines: ~58
- Private/helpers at top level (count): 0
- Best-effort AST + docstring lift; not a line-faithful clone of implementation.
- Open: precise privileges, edge refusals, and test obligations — see product SPEC / tests in source tree.
