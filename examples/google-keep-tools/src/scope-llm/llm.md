# llm

Kind: leaf
Code file: `llm.py`
Collection: `src/scope-llm/`

## Purpose

Shared LLM client stack (HTTP, keys, parse helpers).

## Does

Public callables (names observed at decompile):
- `debug_enabled`
- `debug_log`
- `llm_timeout_seconds`
- `extract_message_text`
- `parse_json_array_from_llm`
- `llm_chat_body_extras`
- `openai_chat_request`
- `resolve_llm_api_key`
- `llm_api_key`
- `default_base_url_for_key_source`
- `default_llm_client`

Types:
- `PhaseTimer` — `mark`, `summary`
- `LLMClient` — `propose_moves`
- `MockLLMClient` — `propose_moves`
- `_RefuseRedirects` — `redirect_request`
- `HttpLLMClient` — `propose_moves`

## Checks

- Module remains a single file (`llm.py`) with the responsibilities above.
- Behavior matches google-keep-tools SPEC/CLI expectations for this surface when applicable.

# Agent

## Decompile
- From: `/Users/stevecoffee/projects/google-keep-tools/llm.py`
- Lines: ~548
- Private/helpers at top level (count): 2
- Best-effort AST + docstring lift; not a line-faithful clone of implementation.
- Open: precise privileges, edge refusals, and test obligations — see product SPEC / tests in source tree.
