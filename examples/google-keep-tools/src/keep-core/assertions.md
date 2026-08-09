# assertions

Kind: leaf
Code file: `assertions.py`
Collection: `src/keep-core/`

## Purpose

Defensive assertions for write operations. See SPEC.md §2 (defensive assertions).

## Scope

**In scope** (belongs here):
- Post-write defensive verify helpers against Keep server state

**Out of scope** (belongs elsewhere — reject as content of this node):
- Business mutations themselves
- CLI

## Does

Public callables (names observed at decompile):
- `deep_verify`
- `fresh_list`
- `verify_list`
- `verify_mode`
- `snapshot`
- `fail`
- `count_delta`
- `item_exists`
- `gained_item`
- `checked_state`
- `group_intact`
- `sibling_sequence`
- `position`
- `sibling_order`
- `structure_unchanged`
- `text_preserved`
- `check_all`
- `verify`
- `retry_until`
- `verify_write`

## Checks

- Module remains a single file (`assertions.py`) with the responsibilities above.
- Behavior matches google-keep-tools SPEC/CLI expectations for this surface when applicable.

# Agent

## Decompile
- From: `/Users/stevecoffee/projects/google-keep-tools/assertions.py`
- Lines: ~393
- Private/helpers at top level (count): 1
- Best-effort AST + docstring lift; not a line-faithful clone of implementation.
- Open: precise privileges, edge refusals, and test obligations — see product SPEC / tests in source tree.
