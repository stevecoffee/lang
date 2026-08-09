# local_eval

Kind: leaf
Code file: `local_eval.py`
Collection: `src/scope-llm/`

## Purpose

Local Ollama evaluation helpers for GKT propose → plans dry-run.

## Scope

**In scope** (belongs here):
- Local model evaluation harness for scope/LLM experiments

**Out of scope** (belongs elsewhere — reject as content of this node):
- Production extract path
- Keep mutations

## Does

Public callables (names observed at decompile):
- `parse_model_list`
- `models_for_eval`
- `local_eval_enabled`
- `restore_local_env`
- `apply_local_ollama_env_defaults`
- `ollama_reachable`
- `ollama_model_names`
- `model_available`
- `new_run_dir`
- `append_result_jsonl`
- `eval_one_model`
- `run_eval`

## Checks

- Module remains a single file (`local_eval.py`) with the responsibilities above.
- Behavior matches google-keep-tools SPEC/CLI expectations for this surface when applicable.

# Agent

## Decompile
- From: `/Users/stevecoffee/projects/google-keep-tools/local_eval.py`
- Lines: ~400
- Private/helpers at top level (count): 3
- Best-effort AST + docstring lift; not a line-faithful clone of implementation.
- Open: precise privileges, edge refusals, and test obligations — see product SPEC / tests in source tree.
