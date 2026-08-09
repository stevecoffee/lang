---
name: metadecompile
description: >
  Closed-context MetaCode decompile: one source code file → one leaf meta
  file. Use for /metadecompile or lifting a single file. Do not fuse a whole
  program into one mega-meta leaf.
---

# MetaDecompile (closed context) — one code file → one leaf meta

## MVP rule

**One source code file decompiles into one leaf MetaCode file.**

Collections (parents that group leaves) are a separate step after per-file leaves exist.

## Context rules (mandatory)

**You may read and use only:**

1. **Language definition** (`docs/language.md`)  
2. **One** declared code file  
3. **This skill**  

**You must not:**

- Read undeclared paths or golden meta on blind lifts  
- Paste the whole file as meta prose  
- Produce multiple leaf files from one code file (MVP)  
- Edit unrelated meta user zones  

## Procedure

1. Read the one code file.  
2. Emit **one** leaf MetaCode file: purpose, **intended in/out scope**, invariants, decisive contracts, checks.  
3. If the current code **violates** that intended boundary: keep the boundary clear, then **enumerate violations** (what is in this file but out of scope). This pattern is **decompile-only** — not for greenfield authoring.  
4. Optional `# Agent`: needs split, proposed leaves, symbol notes.  
5. Optional decompile report: path mapping, unknowns, split recommendations.  
6. Remind: **compile requires clean boundaries** (no violation lists) — violation lists are a lift artifact, not a compile input.

## Output contract

| Output | Required |
|--------|----------|
| One leaf MetaCode file (constraint-shaped) | Yes |
| One code file in → one meta file out | Yes |
| Complete enumeration of helpers/behaviors as the main content | **No** |
| Whole-program mega-meta from one file | **No** |

## Success criteria

- Mapping is obvious: code path ↔ meta path  
- A compiler could satisfy the constraints without the meta narrating every line  
- Unknowns marked, not faked  
