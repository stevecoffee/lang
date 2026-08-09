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
2. Build a **hierarchical MetaCode** tree matching the language definition’s essential components:
   - Purpose (only if evidenced)  
   - Architecture  
   - Surface  
   - Behavior + tests (same coin; scenarios from tests and observed behavior)  
   - Data / state  
   - Infra (only if present)  
   - Non-goals / unknowns  
3. Prefer **contracts, names, and behavior** over algorithms and file chatter.  
4. Apply **no redundancy**: each fact once, refined downward.  
5. Emit MetaCode to the path the operator specifies.  
6. Optionally emit `DECOMPILE_REPORT.md` with source set, unknowns, and confidence notes.

## Output contract

| Output | Required |
|--------|----------|
| MetaCode in language shape | Yes |
| Human-editable hierarchy | Yes |
| Verbatim code paste as meta body | **No** |
| Unknowns called out | Yes when uncertain |

## Success criteria

- Another agent could **compile** this meta under closed context toward behavioral parity  
- Meta is pleasant for a human to edit  
- No undeclared inputs were used  
