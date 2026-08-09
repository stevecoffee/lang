# Playbook: file decompile

MVP: **one code file → one leaf meta file.**

## Inputs (only these)

| Input | Notes |
|-------|--------|
| `docs/language.md` | Language definition |
| One code file | Declared path only |
| `skills/metadecompile/SKILL.md` | Skill |

## Steps

1. Fresh agent turn.  
2. Run metadecompile → one leaf MetaCode file.  
3. Optionally add collection parents later to group leaves.  

## Forbidden

- Whole-repo undeclared reads  
- One mega-meta for many code files in a single leaf (MVP)  
