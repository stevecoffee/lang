# errors

Kind: leaf
Code file: `errors.py`
Collection: `src/keep-core/`

## Purpose

Shared user-facing error hierarchy for google-keep-tools.

## Scope

**In scope** (belongs here):
- Shared GktError hierarchy for expected operator/data failures

**Out of scope** (belongs elsewhere — reject as content of this node):
- Assertion/server-verify helpers (assertions)
- Feature logic

## Does

- Facade / re-exports or constants only (few or no public functions at module top level).

Types:
- `GktError` — (methods omitted)

## Checks

- Module remains a single file (`errors.py`) with the responsibilities above.
- Behavior matches google-keep-tools SPEC/CLI expectations for this surface when applicable.

# Agent

## Decompile
- From: `/Users/stevecoffee/projects/google-keep-tools/errors.py`
- Lines: ~20
- Private/helpers at top level (count): 0
- Best-effort AST + docstring lift; not a line-faithful clone of implementation.
- Open: precise privileges, edge refusals, and test obligations — see product SPEC / tests in source tree.
