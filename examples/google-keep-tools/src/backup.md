# backup

Kind: collection (file `src/backup.md` + directory `src/backup/` — does not compile to a code file)

## Purpose

google-keep-tools modules for **backup**.

## Scope

**In scope** (belongs here):
- Snapshot/package capture of Keep lists, inventory, restore-plan generation
- Backup path safety and private file write rules used only for backups

**Out of scope** (belongs elsewhere — reject as content of this node):
- Live Keep mutations other than read-for-backup (no item edit/xmove here)
- Applying restore plans (plan apply lives in extract-plan/plans)
- CLI argv parsing for backup (cli/backup_cli)
- General config/LLM/scope scoring

## Children

- [backup](backup/backup.md) ← `backup.py`
- [backup_format](backup/backup_format.md) ← `backup_format.py`
- [backup_io](backup/backup_io.md) ← `backup_io.py`
- [backup_restore](backup/backup_restore.md) ← `backup_restore.py`

# Agent

- Collection file is `src/backup.md` (sibling of directory `src/backup/`); children are only inside `backup/`.
- Grouping is by concern, not original source tree paths.
