---
name: metacompile
description: >
  Closed-context MetaCode leaf compile: one leaf meta file → exactly one
  source code file. Use for /metacompile or implementing a leaf. Not for
  ambient repo coding or rewriting user meta above # Agent.
---

# MetaCompile (closed context) — leaf → one code file

## MVP rule

**One leaf MetaCode file compiles into exactly one source code file.**

Collection meta files do **not** emit code; they only provide context / grouping.

## Context rules (mandatory)

**You may read and use only:**

1. **Language definition** (`docs/language.md`)  
2. **One leaf** MetaCode file (the compile target)  
3. Optional **parent collection** meta files if the operator explicitly includes them for context  
4. **This skill**  

**You must not:**

- Read `SPEC.md`, unrelated repo files, or ambient chat requirements  
- Edit user text above `# Agent` in any meta file  
- Emit **multiple** peer source files from one leaf  
- Invent other modules that should be separate leaves (put that in the report as “needs its own leaf”)  

Meta states **constraints**, not a full coding script.  
The leaf must have clear **in scope / out of scope** (or equivalent boundary). If missing, report gap — do not invent a kitchen-sink file.  
Missing *implementation inside this file* → choose within constraints, report it.  
Missing *constraints this file must honor* → report gap; do not invent major product scope.  
Do not require a complete function roster in meta.  
Do not pull in responsibilities the meta marks out of scope (those belong to other leaves).

## Procedure

1. Confirm the target meta is a **leaf** (file-shaped unit). If it is still a whole-app blob, refuse emit and report: split into leaves first.  
2. Honor user-zone **constraints**; use `# Agent` only as non-authoritative notes.  
3. Fill all free decisions so the constraints hold; emit **exactly one** code file.  
4. Emit tests that prove the constraints (not a second novel).  
5. Write compile report: output path, free choices, gaps, “should be other leaves.”

## Output contract

| Output | Required |
|--------|----------|
| **Exactly one** primary source file | Yes |
| Compile report | Yes |
| Extra peer source modules for other concerns | **No** |

## Success criteria

- 1:1 leaf meta ↔ code file respected  
- Closed context; no user-zone edits  
- Gaps reported instead of silent product invention  
