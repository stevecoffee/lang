# Playbook: leaf compile

MVP: **one leaf meta → one code file.** Collections do not emit.

## Inputs (only these)

| Input | Notes |
|-------|--------|
| `docs/language.md` | Language definition |
| One **leaf** MetaCode file | e.g. not the whole-app collection until refined |
| Optional parent collections | Context only |
| `skills/metacompile/SKILL.md` | Skill |

## Steps

1. Fresh agent turn.  
2. If the meta is still a collection / whole product, **stop** — split to leaves first.  
3. Run metacompile → exactly one source file under e.g. `examples/<name>/machine/`.  
4. Read compile report for choices and “needs other leaves.”  

## Forbidden

- Ambient chat requirements  
- Editing user text above `# Agent`  
- Multi-file emit from one leaf  
