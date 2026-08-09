# lang

Intermediate higher-level coding language (working name: **MetaCode**).

> **Meta is source. AI write is compile. Classic code is machine language.**

Product contract: [`SPEC.md`](SPEC.md)  
Keep work list: **Meta coding language project** (`gkt list find-by-repo`)

## Layout

```text
lang/
├── SPEC.md                 # product contract (not default compile context)
├── README.md
├── docs/
│   ├── language.md         # LOADABLE language definition (compile/decompile input)
│   └── playbooks/
│       ├── compile.md      # how to run a compile
│       └── decompile.md    # how to run a decompile
├── skills/
│   ├── metacompile/        # closed-context compile skill
│   └── metadecompile/      # closed-context decompile skill
└── examples/
    └── todo/               # full-screen todo editor (first example)
        ├── README.md
        ├── meta.md         # MetaCode source
        └── machine/        # emitted classic code (after compile; empty until then)
```

## Closed-context runs

Compile and decompile are **skills/prompts**, not ambient chat and not a scripted toolchain yet.

| Op | Agent may see |
|----|----------------|
| **Compile** | `docs/language.md` + MetaCode only (e.g. `examples/todo/meta.md`) + compile skill |
| **Decompile** | `docs/language.md` + **declared** sources only + decompile skill |

Do **not** load full `SPEC.md`, unrelated repo files, or chat lore into a pure run. See SPEC §1.1–1.2.

## Quick start (Phase 1)

1. Read `SPEC.md` (humans / product work).  
2. Edit `docs/language.md` and `examples/todo/meta.md` as the language takes shape.  
3. Run compile via `skills/metacompile` (see `docs/playbooks/compile.md`).  
4. Emit into `examples/todo/machine/`; verify with the host test runner.  
5. Refine language def from gaps — not by widening agent context.
