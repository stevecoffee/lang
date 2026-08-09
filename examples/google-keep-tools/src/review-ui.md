# review-ui

Kind: collection (file `src/review-ui.md` + directory `src/review-ui/` — does not compile to a code file)

## Purpose

google-keep-tools modules for **review-ui**.

## Scope

**In scope** (belongs here):
- Interactive TTY forms/state for params and extract review

**Out of scope** (belongs elsewhere — reject as content of this node):
- Non-interactive library scoring/apply
- CLI argparse (cli/*)
- Keep writes except by calling library after UI confirms

## Children

- [params_ui](review-ui/params_ui.md) ← `params_ui.py`
- [review_ui](review-ui/review_ui.md) ← `review_ui.py`
- [review_state](review-ui/review_state.md) ← `review_state.py`

# Agent

- Collection file is `src/review-ui.md` (sibling of directory `src/review-ui/`); children are only inside `review-ui/`.
- Grouping is by concern, not original source tree paths.
