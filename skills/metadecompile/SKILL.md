---
name: metadecompile
description: >
  Closed-context MetaCode decompile run: lift declared classic sources into
  hierarchical MetaCode using only the language definition. Use when decompiling,
  lifting a codebase to meta, or /metadecompile. Do not use for free-form summary.
---

# MetaDecompile (closed context)

You are executing a **pure decompile** from declared classic sources into MetaCode.

## Context rules (mandatory)

**You may read and use only:**

1. The **language definition** file provided for this run (default: `docs/language.md`)  
2. The **declared source set** for this run (explicit paths of code, tests, and/or docs — nothing else)  
3. **This skill** text  

**You must not:**

- Read undeclared paths, `SPEC.md`, golden meta (on blind lifts), or unrelated files  
- Paste implementation into meta as a line-oriented code dump  
- Invent product goals not evidenced in the declared sources  
- Use chat lore about what the system “should” do  

If sources are incomplete, record **unknowns** rather than fabricating certainty.

## Procedure

1. Inventory declared sources (modules, surfaces, tests, persistence).  
2. Emit **short** MetaCode a human can hold in working memory (language §2.1 budget): What, Not, Shape, Does, Check — more detail only as child nodes if needed.  
3. Prefer **behavior and shape** over file tours and algorithm dumps.  
4. **No redundancy**; don’t invent scenario IDs or module tables unless they clarify.  
5. Emit MetaCode to the path the operator specifies.  
6. Optionally emit `DECOMPILE_REPORT.md` with source set, unknowns, confidence.

## Output contract

| Output | Required |
|--------|----------|
| Short, human-editable MetaCode | Yes |
| Within working-memory budget at each file | Yes |
| Verbatim code paste as meta | **No** |
| Unknowns called out | Yes when uncertain |

## Success criteria

- A developer would actually keep this meta as the mental model  
- Compile could rebuild behavior under closed context  
- No undeclared inputs were used  
