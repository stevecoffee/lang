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
2. Emit **one** leaf MetaCode file: what this file is for, what it does, rules, checks — human-editable, not a line tour.  
3. Include `# Agent` only if needed for unknowns/assumptions about unclear code.  
4. Optional short decompile report: path mapping, unknowns.

## Output contract

| Output | Required |
|--------|----------|
| One leaf MetaCode file | Yes |
| One code file in → one meta file out | Yes |
| Whole-program mega-meta from one file | **No** |

## Success criteria

- Mapping is obvious: code path ↔ meta path  
- Leaf could recompile to one file under metacompile  
- Unknowns marked, not faked  
