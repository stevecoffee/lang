# Decompile report — google-keep-tools

## Source

- Path: `/Users/stevecoffee/projects/google-keep-tools`
- Scope this pass: production root-level (and package) `*.py` excluding `tests/`, `scripts/`, venv
- Date: 2026-08-09
- Language def: `docs/language.md` v0.5 (leaf ↔ one code file)

## Method

1. Inventory production modules via filesystem.
2. AST parse each file: module docstring, top-level functions/classes.
3. Emit one leaf MetaCode file per module under `leaves/`.
4. Build collection parents by concern (cli, keep-core, …).
5. Root collection `L0.google-keep-tools.md` from product purpose (SPEC north star + tree).

## Output map

| Code file | Leaf meta |
|-----------|-----------|
| `assertions.py` | `leaves/assertions.py.md` |
| `auth.py` | `leaves/auth.py.md` |
| `backup.py` | `leaves/backup.py.md` |
| `backup_cli.py` | `leaves/backup_cli.py.md` |
| `backup_format.py` | `leaves/backup_format.py.md` |
| `backup_io.py` | `leaves/backup_io.py.md` |
| `backup_restore.py` | `leaves/backup_restore.py.md` |
| `clear_sandbox.py` | `leaves/clear_sandbox.py.md` |
| `cli_common.py` | `leaves/cli_common.py.md` |
| `config.py` | `leaves/config.py.md` |
| `config_llm.py` | `leaves/config_llm.py.md` |
| `config_paths.py` | `leaves/config_paths.py.md` |
| `config_settings.py` | `leaves/config_settings.py.md` |
| `dump_list.py` | `leaves/dump_list.py.md` |
| `errors.py` | `leaves/errors.py.md` |
| `extract.py` | `leaves/extract.py.md` |
| `extract_apply.py` | `leaves/extract_apply.py.md` |
| `extract_prepare.py` | `leaves/extract_prepare.py.md` |
| `extract_score.py` | `leaves/extract_score.py.md` |
| `get_token.py` | `leaves/get_token.py.md` |
| `gkt.py` | `leaves/gkt.py.md` |
| `item_cli.py` | `leaves/item_cli.py.md` |
| `items.py` | `leaves/items.py.md` |
| `keep_auth.py` | `leaves/keep_auth.py.md` |
| `labels.py` | `leaves/labels.py.md` |
| `list_cli.py` | `leaves/list_cli.py.md` |
| `list_meta.py` | `leaves/list_meta.py.md` |
| `list_notes.py` | `leaves/list_notes.py.md` |
| `lists.py` | `leaves/lists.py.md` |
| `llm.py` | `leaves/llm.py.md` |
| `local_eval.py` | `leaves/local_eval.py.md` |
| `meta_parse.py` | `leaves/meta_parse.py.md` |
| `meta_repo.py` | `leaves/meta_repo.py.md` |
| `meta_snapshot.py` | `leaves/meta_snapshot.py.md` |
| `meta_style.py` | `leaves/meta_style.py.md` |
| `meta_write.py` | `leaves/meta_write.py.md` |
| `params_ui.py` | `leaves/params_ui.py.md` |
| `path_confine.py` | `leaves/path_confine.py.md` |
| `plan_cli.py` | `leaves/plan_cli.py.md` |
| `plans.py` | `leaves/plans.py.md` |
| `propose.py` | `leaves/propose.py.md` |
| `purge_sandbox.py` | `leaves/purge_sandbox.py.md` |
| `reorg_rules.py` | `leaves/reorg_rules.py.md` |
| `review_state.py` | `leaves/review_state.py.md` |
| `review_ui.py` | `leaves/review_ui.py.md` |
| `scope_score.py` | `leaves/scope_score.py.md` |
| `scope_score_hit.py` | `leaves/scope_score_hit.py.md` |
| `scope_score_llm.py` | `leaves/scope_score_llm.py.md` |
| `scope_score_run.py` | `leaves/scope_score_run.py.md` |
| `score_cache.py` | `leaves/score_cache.py.md` |

## Not decompiled this pass

- `tests/**` (~30 modules) — large; treat as separate collection later
- `scripts/**`
- Non-Python: docs, TOML samples, plans/, snapshots/
- Secrets/state files (`keep-state.json`, credentials) — never meta targets

## Unknowns / quality limits

- Leaf text is **summary**, not full behavioral contract from tests
- Cross-module call graph not fully modeled in meta
- Privilege matrices and refusal tables still live in product SPEC, not duplicated into every leaf
- Some facades (`backup.py`, `config.py`, `extract.py`) re-export; leaves note facade role

## Assumptions

- Production layout stays flat package of modules at repo root
- One leaf ↔ one of those `.py` files (MVP)
- Collections are agent/product navigation only

## Next iterations

1. Decompile key tests as leaves under `leaves/tests__…`
2. Human pass: pin user-zone facts on critical leaves (`items.py`, `lists.py`, `gkt.py`)
3. Optional: import graph edges in Agent sections
