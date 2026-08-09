# Todo — meta index

Hierarchy (product → code). Format informal; content first.

| Layer | File | Role |
|-------|------|------|
| L0 | [L0.md](L0.md) | Product — what it is |
| L1 | [L1.md](L1.md) | Behavior — what you can do |
| L2 | [L2.md](L2.md) | Architecture — main parts |
| L3 | [L3.md](L3.md) | Detailed design — enough to implement |
| L4 | [machine/](machine/) | Classic code (emit target; empty until compile) |

**Implementer handoff:** language def + L0…L3 (or L3 + parents) + compile skill → `machine/`.

Original root sketch is expanded into L0; bindings and list behavior live in L1+.
