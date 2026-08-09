# MetaCode — language definition (loadable)

**Status:** stub / Phase 1  
**Audience:** humans authoring meta; agents on **compile** and **decompile** runs  
**Not this file:** product phases, Keep process, someday chrome — those live in `SPEC.md` and must **not** be loaded as compile context.

This document is the **compiler-facing** language definition. A pure compile run’s project-specific input is only this file (or its successor) plus the MetaCode artifact.

Working names: **MetaCode** (language), **MetaCompiler** / compile skill (emit), **MetaBDD** (tests co-specified with code). Better names TBD.

---

## 1. Thesis

**Meta is source. AI write is compile. Classic code is machine language.**

| Layer | Role |
|-------|------|
| MetaCode | Primary authoring surface — hierarchical intent, structure, tests |
| Compile | Structure-led emit to classic code (+ tests); model fills bodies |
| Classic code | Executable substrate (TS, Python, …) |

---

## 2. Artifact model

- A MetaCode unit is a **node in a refinement tree**, not classic code with comments.
- Hierarchy is nested headings and/or separate files for children.
- **Parents** hold what you keep in your head for that unit; **children** hold detail only when someone is working that part.
- **Condense** upward; **expand** downward. Never paste the whole system into one flat essay.
- Compile may use one subtree at a time so a run stays small.

### 2.1 Progressive disclosure (working-memory budget)

Meta exists to **simplify the mental model**, not to front-load every design decision.

A developer is not holding modules, timestamps, scenario IDs, and infra notes all at once. Meta must match that.

**Soft limits per MetaCode file** (like a line-count budget for code files) — revise numbers if practice demands, but keep *a* budget:

| Budget | Guideline |
|--------|-----------|
| Length | About **one screen** when skimming (~40–60 lines); flag if much longer |
| Top-level sections | At most **~7** |
| Bullets per section | At most **~7** |
| Concepts on the page | Only what you need to **explain or change this unit today** |

**Detail goes down, not sideways.** Module lists, field catalogs, keybindings, scenario matrices → child nodes or later expansion when that layer is in focus — not the root file “just in case.”

**Root of an app** should read like a sharp product pitch + shape + does/check — not a design doc dump.

### 2.2 What a unit usually answers (not a forced outline)

Cover these **as briefly as truth allows**. Do **not** open a long section for each if one line will do.

| Concern | In plain terms |
|---------|----------------|
| What is it? | One or two sentences |
| Not this | Out of scope (short) |
| Shape | Main parts, data you care about, where it lives |
| Does | Behaviors (and checks live here or as “same as does”) |
| Stack / deps | Only if needed to build or run |

Architecture diagrams, module tables, and infra appear **when the unit is about that**, or as children of Shape — not as mandatory ceremony.

---

## 3. Hard rules

### 3.1 Structure owns skeleton; model fills flesh

- Where meta **names** parts, layout, or public surface, compile must honor them.
- Where meta stays silent, compile may choose reasonable structure and must record choices in the compile report — **do not** force authors to pre-list every module to get a first build.
- Prefer meta that states **intent and shape** over meta that micro-specifies files.

### 3.2 Code and tests are one coin

- Prefer **Does** + **Check** (or “check = does, including after restart”) over a parallel test novel and scenario ID catalogs.
- Extra fixed cases only when they are not obvious from Does.

### 3.3 No redundancy

- Each fact **once**. Refine in children; do not restate in siblings.

### 3.4 Embed, don’t doc-drift

- Machine code carries intent via naming/structure; not a second hand-maintained doc tree.

### 3.5 Simple as possible

- Prefer plain language a human will actually edit.
- Prefer hierarchical Markdown until formal grammar is justified.
- Closed-context skills before custom parser/codegen.

### 3.6 Prefer obvious over cryptic

- No fake precision (S1…S12, internal codenames) unless it helps a human.
- Short words beat framework jargon when both mean the same thing.

---

## 4. Compile semantics

```text
compile(language_definition, metacode) → machine_code + tests + compile_report
```

**Allowed inputs:** this language definition; the MetaCode unit; the compile skill text.  
**Forbidden (greenfield):** ambient chat; unrelated repo files; full product SPEC; existing machine code.

**Compile must:**

1. Honor names/layout/surface **when meta states them**; otherwise choose simply and report choices.  
2. Emit classic code + tests aligned with **Does/Check** (not a missing scenario encyclopedia).  
3. Prefer asking via compile report over inventing product scope.  
4. Produce a short **compile report**: choices, gaps, conflicts, questions.

**Brownfield** (meta + existing machine + drift rules) is a **separate mode** — not default greenfield compile.

---

## 5. Decompile semantics

```text
decompile(language_definition, declared_sources) → metacode [+ unknowns]
```

**Allowed inputs:** this language definition; **only** sources the run declares (e.g. listed paths of code/tests/docs); the decompile skill text.  
**Forbidden:** undeclared paths; golden meta on blind lifts; chat goals not in sources.

**Decompile must:**

1. Emit MetaCode in the shape this definition describes (hierarchy + essential components).  
2. Capture enough for a later compile toward **behavioral** clone — not a code paste or prose dump.  
3. Prefer structure and contracts over line-level narration.  
4. Record unknowns / low confidence when the language allows (do not invent certainty).

---

## 6. Output conventions (stub)

- Example projects live under `examples/<name>/`.  
- MetaCode default path: `examples/<name>/meta.md` (or `meta/` tree later).  
- Emitted machine code default path: `examples/<name>/machine/`.  
- Host language for a given example is declared in that example’s meta (or README); one host per early example.

*Refine naming/embed conventions here as the first example teaches them.*

---

## 7. Document control

| Version | Notes |
|---------|--------|
| 0.1-stub | Initial loadable def split from SPEC |
| 0.2 | Working-memory budget / progressive disclosure; thinner root meta; less forced ceremony |
