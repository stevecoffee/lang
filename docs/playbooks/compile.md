# Playbook: compile run

Closed-context **greenfield** compile. Product background: `SPEC.md` §1.1–1.2 (do **not** feed SPEC into the agent).

## Goal

```text
compile(language_definition, metacode) → machine_code + tests + compile_report
```

## Inputs (only these)

| Input | Path (repo defaults) |
|-------|----------------------|
| Language definition | `docs/language.md` |
| MetaCode | e.g. `examples/todo/meta.md` |
| Skill | `skills/metacompile/SKILL.md` |

## Forbidden

- Full `SPEC.md`, Keep notes, chat history, “also do X”
- Unrelated repo files
- Existing `machine/` tree as authority (greenfield: emit fresh or replace generated outputs only as skill states)
- Inventing modules/APIs not present in meta

## Steps

1. Start a **fresh** agent turn / subagent (no inherited thread).  
2. Load **only** the three inputs above.  
3. Invoke the metacompile skill procedure.  
4. Write machine code + tests under the example’s `machine/` (or path meta declares).  
5. Write a short compile report next to the emit (e.g. `machine/COMPILE_REPORT.md`).  
6. Run host typecheck/tests outside the pure compile context if available.  
7. If the model needed undeclared facts, **fix language def or meta** — do not widen context next time.

## Brownfield

Not this playbook. Use a separate brownfield skill/mode when defined (meta + declared existing machine + reconcile rules).

## Checklist

- [ ] Fresh context  
- [ ] Only language def + meta + skill  
- [ ] Structure/names match meta  
- [ ] Tests co-emitted from meta scenarios  
- [ ] Compile report written  
- [ ] Gaps filed into language def or meta (not into chat lore)
