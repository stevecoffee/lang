# Playbook: decompile run

Closed-context lift from declared sources into MetaCode. Product background: `SPEC.md` §1.1–1.2 (do **not** feed SPEC into the agent).

## Goal

```text
decompile(language_definition, declared_sources) → metacode [+ unknowns]
```

## Inputs (only these)

| Input | Path (repo defaults) |
|-------|----------------------|
| Language definition | `docs/language.md` |
| Declared sources | Explicit path list (code, tests, docs) — pinned for the run |
| Skill | `skills/metadecompile/SKILL.md` |

## Forbidden

- Undeclared repo paths  
- Golden/reference meta on **blind** lifts  
- Ambient chat goals not evidenced in sources  
- Full `SPEC.md` as input  

## Steps

1. Start a **fresh** agent turn / subagent.  
2. Write down the **declared source set** (paths) before the run.  
3. Load **only** language def + those sources + decompile skill.  
4. Emit MetaCode in the language’s shape (e.g. `examples/<name>/meta.md` or a trial path).  
5. Optionally attach unknowns / confidence if the skill requires it.  
6. Critique: could a compile skill rebuild behavior without code paste?  
7. Fold gaps into `docs/language.md` — do not keep them as chat-only lore.

## Blind lift (language test)

When testing the language: hide any hand-written golden meta; declare only machine sources; compare lift to golden offline (outside the decompile agent).

## Checklist

- [ ] Fresh context  
- [ ] Declared source set written down  
- [ ] Only language def + declared sources + skill  
- [ ] Meta is hierarchical and editable  
- [ ] Not a line-by-line code paraphrase  
- [ ] Unknowns recorded rather than faked  
