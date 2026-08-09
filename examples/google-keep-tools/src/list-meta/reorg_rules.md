# reorg_rules

Kind: leaf
Code file: `reorg_rules.py`
Collection: `src/list-meta/`

## Purpose

Seed/verify the Keep reorg rules list (human-readable operator notes).

## Does

Public callables (names observed at decompile):
- `find_rules_list`
- `list_rule_texts`
- `seed_reorg_rules`

## Checks

- Module remains a single file (`reorg_rules.py`) with the responsibilities above.
- Behavior matches google-keep-tools SPEC/CLI expectations for this surface when applicable.

# Agent

## Decompile
- From: `/Users/stevecoffee/projects/google-keep-tools/reorg_rules.py`
- Lines: ~111
- Private/helpers at top level (count): 0
- Best-effort AST + docstring lift; not a line-faithful clone of implementation.
- Open: precise privileges, edge refusals, and test obligations — see product SPEC / tests in source tree.
