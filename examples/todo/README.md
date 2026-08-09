# Example: full-screen todo editor

First Phase 1 example system for MetaCode.

## Intent

Full-screen **text** todo app: list of items, keyboard-driven. Meta is plain-language product truth (fine for non-programmers). Implementation is chosen at compile time.

**Hierarchy:** `meta.md` may use **sections as stand-ins** for child nodes; multi-file meta comes later. Format is informal until content settles.

## Paths

| Artifact | Path |
|----------|------|
| MetaCode (source of truth) | [`meta.md`](meta.md) |
| Emitted machine code | [`machine/`](machine/) — empty until a compile run |
| Language definition | [`../../docs/language.md`](../../docs/language.md) |
| Compile skill | [`../../skills/metacompile/SKILL.md`](../../skills/metacompile/SKILL.md) |
| Decompile skill | [`../../skills/metadecompile/SKILL.md`](../../skills/metadecompile/SKILL.md) |

## Host language

**TBD** (open decision D2). Declare the choice in `meta.md` under Architecture when locked. Prefer one of: TypeScript or Python; UI may be terminal full-screen (TUI) or simple web full-viewport — pick one stack when compiling, record it in meta.

## Compile (closed context)

See [`docs/playbooks/compile.md`](../../docs/playbooks/compile.md).

Agent inputs **only**:

1. `docs/language.md`  
2. `examples/todo/meta.md`  
3. `skills/metacompile/SKILL.md`  

Emit into `examples/todo/machine/`.

## Status

- [x] Directory stub  
- [x] Meta skeleton (`meta.md`)  
- [ ] Meta filled enough for first compile  
- [ ] First closed-context compile run  
- [ ] Host tests green  
