# get_token

Kind: leaf
Code file: `get_token.py`
Collection: `keep-core/`

## Purpose

Exchange a Google `oauth_token` for a gkeepapi master token.

## Does

Public callables (names observed at decompile):
- `read_oauth_token`
- `exchange_master_token`

## Checks

- Module remains a single file (`get_token.py`) with the responsibilities above.
- Behavior matches google-keep-tools SPEC/CLI expectations for this surface when applicable.

# Agent

## Decompile
- From: `/Users/stevecoffee/projects/google-keep-tools/get_token.py`
- Lines: ~123
- Private/helpers at top level (count): 0
- Best-effort AST + docstring lift; not a line-faithful clone of implementation.
- Open: precise privileges, edge refusals, and test obligations — see product SPEC / tests in source tree.
