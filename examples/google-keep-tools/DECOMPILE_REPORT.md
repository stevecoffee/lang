# Decompile report — google-keep-tools

## Source

- Path: `/Users/stevecoffee/projects/google-keep-tools`
- Production `*.py` (not tests/scripts)

## Layout

Example root:

- `meta.md` — product collection
- `README.md`, `DECOMPILE_REPORT.md`
- `machine/` — emit sink
- **`src/`** — all collection pairs (decompile-of-source body)

Under `src/`, each collection is a **file + directory pair**:

- `src/backup.md` — collection meta
- `src/backup/` — leaf children only

Leaves named by module stem (`src/backup/backup_format.md` ↔ `backup_format.py`).
Grouping by concern, not original paths.

## Map

| Code file | Meta leaf |
|-----------|----------|
| `gkt.py` | `src/cli/gkt.md` |
| `cli_common.py` | `src/cli/cli_common.md` |
| `list_cli.py` | `src/cli/list_cli.md` |
| `item_cli.py` | `src/cli/item_cli.md` |
| `plan_cli.py` | `src/cli/plan_cli.md` |
| `backup_cli.py` | `src/cli/backup_cli.md` |
| `auth.py` | `src/cli/auth.md` |
| `keep_auth.py` | `src/keep-core/keep_auth.md` |
| `get_token.py` | `src/keep-core/get_token.md` |
| `lists.py` | `src/keep-core/lists.md` |
| `items.py` | `src/keep-core/items.md` |
| `labels.py` | `src/keep-core/labels.md` |
| `list_notes.py` | `src/keep-core/list_notes.md` |
| `dump_list.py` | `src/keep-core/dump_list.md` |
| `errors.py` | `src/keep-core/errors.md` |
| `assertions.py` | `src/keep-core/assertions.md` |
| `list_meta.py` | `src/list-meta/list_meta.md` |
| `meta_parse.py` | `src/list-meta/meta_parse.md` |
| `meta_write.py` | `src/list-meta/meta_write.md` |
| `meta_style.py` | `src/list-meta/meta_style.md` |
| `meta_repo.py` | `src/list-meta/meta_repo.md` |
| `meta_snapshot.py` | `src/list-meta/meta_snapshot.md` |
| `reorg_rules.py` | `src/list-meta/reorg_rules.md` |
| `extract.py` | `src/extract-plan/extract.md` |
| `extract_prepare.py` | `src/extract-plan/extract_prepare.md` |
| `extract_score.py` | `src/extract-plan/extract_score.md` |
| `extract_apply.py` | `src/extract-plan/extract_apply.md` |
| `propose.py` | `src/extract-plan/propose.md` |
| `plans.py` | `src/extract-plan/plans.md` |
| `backup.py` | `src/backup/backup.md` |
| `backup_format.py` | `src/backup/backup_format.md` |
| `backup_io.py` | `src/backup/backup_io.md` |
| `backup_restore.py` | `src/backup/backup_restore.md` |
| `config.py` | `src/config-paths/config.md` |
| `config_settings.py` | `src/config-paths/config_settings.md` |
| `config_paths.py` | `src/config-paths/config_paths.md` |
| `config_llm.py` | `src/config-paths/config_llm.md` |
| `path_confine.py` | `src/config-paths/path_confine.md` |
| `llm.py` | `src/scope-llm/llm.md` |
| `scope_score.py` | `src/scope-llm/scope_score.md` |
| `scope_score_hit.py` | `src/scope-llm/scope_score_hit.md` |
| `scope_score_llm.py` | `src/scope-llm/scope_score_llm.md` |
| `scope_score_run.py` | `src/scope-llm/scope_score_run.md` |
| `score_cache.py` | `src/scope-llm/score_cache.md` |
| `local_eval.py` | `src/scope-llm/local_eval.md` |
| `params_ui.py` | `src/review-ui/params_ui.md` |
| `review_ui.py` | `src/review-ui/review_ui.md` |
| `review_state.py` | `src/review-ui/review_state.md` |
| `clear_sandbox.py` | `src/sandbox/clear_sandbox.md` |
| `purge_sandbox.py` | `src/sandbox/purge_sandbox.md` |

## Quality limits

- Constraint-first language preferred; pass-1 leaves may still list public symbols.
- Tests/scripts not decompiled.
- Boundary violation lists are decompile-only; compile requires clean boundaries.
