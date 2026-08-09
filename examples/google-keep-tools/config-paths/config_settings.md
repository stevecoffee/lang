# config_settings

Kind: leaf
Code file: `config_settings.py`
Collection: `config-paths/`

## Purpose

Config load, Settings, TOML search, overrides, and value-resolution helpers.

## Does

Public callables (names observed at decompile):
- `set_file_search`
- `file_search_enabled`
- `set_config_path`
- `config_path_override`
- `set_override`
- `clear_overrides`
- `has_override`
- `reset`
- `candidate_config_paths`
- `find_config_path`
- `load_toml_file`
- `load_settings`
- `get_settings`
- `apply_cli_config_arg`

Types:
- `ConfigError` — (methods omitted)
- `Settings` — `section`, `trusted_for_allow_hosts`

## Checks

- Module remains a single file (`config_settings.py`) with the responsibilities above.
- Behavior matches google-keep-tools SPEC/CLI expectations for this surface when applicable.

# Agent

## Decompile
- From: `/Users/stevecoffee/projects/google-keep-tools/config_settings.py`
- Lines: ~493
- Private/helpers at top level (count): 13
- Best-effort AST + docstring lift; not a line-faithful clone of implementation.
- Open: precise privileges, edge refusals, and test obligations — see product SPEC / tests in source tree.
