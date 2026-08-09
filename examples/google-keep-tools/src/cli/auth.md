# auth

Kind: leaf
Code file: `auth.py`
Collection: `src/cli/`

## Purpose

Verify Google Keep authentication. CLI: ``gkt auth``.

## Scope

**In scope** (belongs here):
- gkt auth handler: verify session

**Out of scope** (belongs elsewhere — reject as content of this node):
- Credential exchange (get_token)
- Keep.login implementation (keep_auth)

## Does

Public callables (names observed at decompile):
- `run_auth`

## Checks

- Module remains a single file (`auth.py`) with the responsibilities above.
- Behavior matches google-keep-tools SPEC/CLI expectations for this surface when applicable.

# Agent

## Decompile
- From: `/Users/stevecoffee/projects/google-keep-tools/auth.py`
- Lines: ~24
- Private/helpers at top level (count): 0
- Best-effort AST + docstring lift; not a line-faithful clone of implementation.
- Open: precise privileges, edge refusals, and test obligations — see product SPEC / tests in source tree.
