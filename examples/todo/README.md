# Example: Todo

Full-screen text todo list.

| File | Role |
|------|------|
| [meta.md](meta.md) | **L0** product — user spec + `# Agent` assumptions/questions |
| [L1.md](L1.md) | **L1** behavior — next hierarchy level |
| [machine/](machine/) | L4 emit target (after compile) |

## User vs Agent

- **User** text (above `# Agent`): human only — do not let agents rewrite it  
- **`# Agent`**: agents may add assumptions, open questions, generated notes  

Rule is in `docs/language.md` §2.4.

## Compile (later)

Closed context: language def + meta nodes + compile skill → `machine/`.  
Prefer L1+ (and deeper when present) for implementer-style runs.
