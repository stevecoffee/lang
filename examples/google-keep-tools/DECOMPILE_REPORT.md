# Decompile report — google-keep-tools

## Source

- Path: `/Users/stevecoffee/projects/google-keep-tools`
- Production `*.py` (not tests/scripts)

## Layout (revised)

Collections are **directories**. Each directory’s `meta.md` describes the collection; sibling `*.md` files are leaves (1 ↔ 1 code file). Names have no layout prefixes.

This does **not** preserve the original source tree; grouping is by concern.

## Map

| Code file | Meta leaf |
|-----------|----------|
| `gkt.py` | `cli/gkt.md` |
| `cli_common.py` | `cli/cli_common.md` |
| `list_cli.py` | `cli/list_cli.md` |
| `item_cli.py` | `cli/item_cli.md` |
| `plan_cli.py` | `cli/plan_cli.md` |
| `backup_cli.py` | `cli/backup_cli.md` |
| `auth.py` | `cli/auth.md` |
| `keep_auth.py` | `keep-core/keep_auth.md` |
| `get_token.py` | `keep-core/get_token.md` |
| `lists.py` | `keep-core/lists.md` |
| `items.py` | `keep-core/items.md` |
| `labels.py` | `keep-core/labels.md` |
| `list_notes.py` | `keep-core/list_notes.md` |
| `dump_list.py` | `keep-core/dump_list.md` |
| `errors.py` | `keep-core/errors.md` |
| `assertions.py` | `keep-core/assertions.md` |
| `list_meta.py` | `list-meta/list_meta.md` |
| `meta_parse.py` | `list-meta/meta_parse.md` |
| `meta_write.py` | `list-meta/meta_write.md` |
| `meta_style.py` | `list-meta/meta_style.md` |
| `meta_repo.py` | `list-meta/meta_repo.md` |
| `meta_snapshot.py` | `list-meta/meta_snapshot.md` |
| `reorg_rules.py` | `list-meta/reorg_rules.md` |
| `extract.py` | `extract-plan/extract.md` |
| `extract_prepare.py` | `extract-plan/extract_prepare.md` |
| `extract_score.py` | `extract-plan/extract_score.md` |
| `extract_apply.py` | `extract-plan/extract_apply.md` |
| `propose.py` | `extract-plan/propose.md` |
| `plans.py` | `extract-plan/plans.md` |
| `backup.py` | `backup/backup.md` |
| `backup_format.py` | `backup/backup_format.md` |
| `backup_io.py` | `backup/backup_io.md` |
| `backup_restore.py` | `backup/backup_restore.md` |
| `config.py` | `config-paths/config.md` |
| `config_settings.py` | `config-paths/config_settings.md` |
| `config_paths.py` | `config-paths/config_paths.md` |
| `config_llm.py` | `config-paths/config_llm.md` |
| `path_confine.py` | `config-paths/path_confine.md` |
| `llm.py` | `scope-llm/llm.md` |
| `scope_score.py` | `scope-llm/scope_score.md` |
| `scope_score_hit.py` | `scope-llm/scope_score_hit.md` |
| `scope_score_llm.py` | `scope-llm/scope_score_llm.md` |
| `scope_score_run.py` | `scope-llm/scope_score_run.md` |
| `score_cache.py` | `scope-llm/score_cache.md` |
| `local_eval.py` | `scope-llm/local_eval.md` |
| `params_ui.py` | `review-ui/params_ui.md` |
| `review_ui.py` | `review-ui/review_ui.md` |
| `review_state.py` | `review-ui/review_state.md` |
| `clear_sandbox.py` | `sandbox/clear_sandbox.md` |
| `purge_sandbox.py` | `sandbox/purge_sandbox.md` |

## Quality limits

- Constraint-first language preferred; pass-1 leaves may still list public symbols (refine later).
- Tests/scripts not decompiled.
