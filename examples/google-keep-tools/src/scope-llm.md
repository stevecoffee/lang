# scope-llm

Kind: collection (file `src/scope-llm.md` + directory `src/scope-llm/` — does not compile to a code file)

## Purpose

google-keep-tools modules for **scope-llm**.

## Scope

**In scope** (belongs here):
- HTTP LLM client, item/list scope scoring, score cache, local model eval harness

**Out of scope** (belongs elsewhere — reject as content of this node):
- Config file schema (config-paths) except reading settings
- Keep mutations (keep-core/items)
- Extract apply/plan apply (extract-plan)
- TTY review UI (review-ui)

## Children

- [llm](scope-llm/llm.md) ← `llm.py`
- [scope_score](scope-llm/scope_score.md) ← `scope_score.py`
- [scope_score_hit](scope-llm/scope_score_hit.md) ← `scope_score_hit.py`
- [scope_score_llm](scope-llm/scope_score_llm.md) ← `scope_score_llm.py`
- [scope_score_run](scope-llm/scope_score_run.md) ← `scope_score_run.py`
- [score_cache](scope-llm/score_cache.md) ← `score_cache.py`
- [local_eval](scope-llm/local_eval.md) ← `local_eval.py`

# Agent

- Collection file is `src/scope-llm.md` (sibling of directory `src/scope-llm/`); children are only inside `scope-llm/`.
- Grouping is by concern, not original source tree paths.
