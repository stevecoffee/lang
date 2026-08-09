---
name: metacompile
description: >
  Closed-context MetaCode compile run: emit classic machine code and tests from
  language definition + MetaCode only. Use when compiling meta, implementing from
  MetaCode, or /metacompile. Do not use for product planning or ambient repo coding.
---

# MetaCompile (closed context)

You are executing a **pure greenfield compile** of MetaCode into classic machine code.

## Context rules (mandatory)

**You may read and use only:**

1. The **language definition** file provided for this run (default in this repo: `docs/language.md`)  
2. The **MetaCode** artifact provided for this run (e.g. `examples/todo/meta.md`)  
3. **This skill** text  

**You must not:**

- Read `SPEC.md`, other examples, playbooks, Keep state, or unrelated repo files  
- Use prior chat instructions that are not written in the MetaCode or language definition  
- Treat existing `machine/` code as a source of new requirements (greenfield emit)  
- Invent modules, public APIs, routes, commands, or file layout not authorized by MetaCode  

Meta may be written by **non-programmers**. Missing *implementation* detail is normal — **you choose it**. Missing *product* behavior is a gap — **report it**, don’t invent major features.

## Procedure

1. Read MetaCode as a **hierarchy** (sections ≈ child nodes; later separate files). Use the unit you were given, not the whole universe.  
2. **Product truth** = what the meta says in plain language (what it is, what you can do, controls, user-visible rules).  
3. **Implementation** (modules, files, frameworks, schemas, algorithms) = your job when meta is silent; keep it simple; list choices in the report.  
4. Honor explicit user-facing rules and described controls (e.g. keybindings).  
5. Emit **tests** from stated/implied behavior.  
6. Write outputs to the path given (default: `examples/<name>/machine/`).  
7. Write `COMPILE_REPORT.md`: implementation choices, product gaps, conflicts, questions.

## Output contract

| Output | Required |
|--------|----------|
| Machine source tree | Yes |
| Tests from meta behavior | Yes |
| `COMPILE_REPORT.md` (esp. implementation choices) | Yes |
| Major product features not in meta | **No** |

## Success criteria

- Non-programmer meta is enough to build something faithful  
- Implementation was filled without demanding meta become code  
- No undeclared inputs; product gaps reported, not silently assumed  
