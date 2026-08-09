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

If information is missing, **fail clearly** in the compile report and emit only what is justified — do not pad from world knowledge about “typical todo apps” beyond meta.

## Procedure

1. Read MetaCode as a **small refinement tree** — prefer short root files; do not demand missing ceremony.  
2. Take **What / Not / Shape / Does / Check** (or equivalent) as authority for product scope.  
3. Where meta **names** parts or layout, honor them. Where it does not, choose a simple structure and list choices in the report.  
4. Emit **tests** from Does/Check (same coin), not from a fictional scenario catalog.  
5. Write outputs to the destination path given by the operator (default: `examples/<name>/machine/`).  
6. Write `COMPILE_REPORT.md`: choices, gaps, conflicts, questions.

## Output contract

| Output | Required |
|--------|----------|
| Machine source tree | Yes |
| Tests from Does/Check | Yes |
| `COMPILE_REPORT.md` | Yes |
| Product scope not in meta | **No** |

## Success criteria

- A human can still read the meta in one screen and recognize the app  
- Does/Check drive product and tests together  
- No undeclared inputs; missing product facts → report, don’t invent scope  
