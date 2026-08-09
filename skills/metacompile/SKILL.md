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

1. Parse MetaCode as a **refinement tree** (headings / hierarchy).  
2. Build the **skeleton**: modules, components, names, public surface, file layout, test shells — all from meta.  
3. Fill **bodies** under that skeleton (algorithms, wiring) without changing the skeleton.  
4. Emit **tests** from co-specified scenarios under the same features (same coin).  
5. Write outputs to the destination path given by the operator (default: `examples/<name>/machine/`).  
6. Write `COMPILE_REPORT.md` in that destination covering:
   - assumptions  
   - any elaborations you believe meta forced vs optional  
   - conflicts or ambiguities  
   - questions for the meta author  

## Output contract

| Output | Required |
|--------|----------|
| Machine source tree | Yes |
| Tests runnable (or clearly marked manual scenarios) | Yes |
| `COMPILE_REPORT.md` | Yes |
| New modules not in meta | **No** |

## Success criteria

- Structure and names are meta-driven and stable under re-run intent  
- A meta edit that changes behavior would require a recompile that changes product and tests together  
- No undeclared inputs were needed; if they were, report that as a language/meta defect  
