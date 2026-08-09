# config_llm

Kind: leaf
Code file: `config_llm.py`
Collection: `config-paths/`

## Purpose

LLM / scope / eval settings getters, API key resolve, host allowlists.

## Does

Public callables (names observed at decompile):
- `llm_base_url`
- `llm_model`
- `llm_timeout`
- `llm_reasoning_effort`
- `llm_allow_hosts`
- `llm_debug`
- `llm_trace_path`
- `scope_model`
- `scope_threshold`
- `label_cache`
- `sandbox_list_id`
- `eval_models_raw`
- `local_eval_enabled`
- `resolve_api_key`
- `default_base_url_for_key_source`
- `resolved_llm_base_url`
- `allowlisted_hosts`

## Checks

- Module remains a single file (`config_llm.py`) with the responsibilities above.
- Behavior matches google-keep-tools SPEC/CLI expectations for this surface when applicable.

# Agent

## Decompile
- From: `/Users/stevecoffee/projects/google-keep-tools/config_llm.py`
- Lines: ~401
- Private/helpers at top level (count): 3
- Best-effort AST + docstring lift; not a line-faithful clone of implementation.
- Open: precise privileges, edge refusals, and test obligations — see product SPEC / tests in source tree.
