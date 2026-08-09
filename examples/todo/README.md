# Example: Todo

| File | Role |
|------|------|
| [L0.Todo.md](L0.Todo.md) | Product root — treat as **collection** until refined into leaves |
| [machine/](machine/) | Emitted code: **one file per compiled leaf** |

## MVP mapping

- **Leaf** meta file ↔ **one** code file (compile / decompile)  
- **Collection** meta (e.g. L0) groups children; does not emit code by itself  
- Agents only edit under `# Agent` in meta files  

See `docs/language.md` v0.5.
