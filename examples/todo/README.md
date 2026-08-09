# Example: Todo

Full-screen text todo list. Meta is a **layer ladder** L0→L3; code is L4 under `machine/`.

## Layers

| File | Layer |
|------|--------|
| [L0.md](L0.md) | Product |
| [L1.md](L1.md) | Behavior |
| [L2.md](L2.md) | Architecture |
| [L3.md](L3.md) | Detailed design |
| [meta.md](meta.md) | Index |
| [machine/](machine/) | L4 emit (after compile) |

Plain language at the top; more design detail as you go down. Non-programmers can stay on L0–L1. Implementer agents use L3 (with parents) under closed context.

## Compile (closed context)

See [`docs/playbooks/compile.md`](../../docs/playbooks/compile.md).

**Implementer-style run** — agent sees only:

1. `docs/language.md`  
2. `examples/todo/L0.md` … `L3.md` (or L3 + short parents)  
3. `skills/metacompile/SKILL.md`  

Emit into `examples/todo/machine/`.

Stack/toolkit still chosen at compile if not pinned in L2/L3; record choices in `COMPILE_REPORT.md`.

## Status

- [x] L0–L3 drafted from root sketch  
- [ ] Human pass on content  
- [ ] First closed-context compile (L3 → machine)  
- [ ] Tests green  
