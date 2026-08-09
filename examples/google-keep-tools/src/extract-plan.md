# extract-plan

Kind: collection (file `src/extract-plan.md` + directory `src/extract-plan/` — does not compile to a code file)

## Purpose

google-keep-tools modules for **extract-plan**.

## Scope

**In scope** (belongs here):
- Reorg extract pipeline: prepare, score selection, apply create_list+moves
- Plan JSONL model, dry-run/apply orchestration, propose helpers

**Out of scope** (belongs elsewhere — reject as content of this node):
- Low-level item/list primitives (keep-core) except as callees
- Backup snapshot format (backup/*)
- Interactive review UI widgets (review-ui/*) except as optional callers
- gkt plan CLI argv (cli/plan_cli)

## Children

- [extract](extract-plan/extract.md) ← `extract.py`
- [extract_prepare](extract-plan/extract_prepare.md) ← `extract_prepare.py`
- [extract_score](extract-plan/extract_score.md) ← `extract_score.py`
- [extract_apply](extract-plan/extract_apply.md) ← `extract_apply.py`
- [propose](extract-plan/propose.md) ← `propose.py`
- [plans](extract-plan/plans.md) ← `plans.py`

# Agent

- Collection file is `src/extract-plan.md` (sibling of directory `src/extract-plan/`); children are only inside `extract-plan/`.
- Grouping is by concern, not original source tree paths.
