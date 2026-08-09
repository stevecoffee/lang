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
- Hierarchy is expressed with nested headings (Markdown) or an equivalent tree of files.
- **Parents** own summary intent and contracts; **children** refine without contradicting parents.
- **Condense** rolls detail upward without dropping requirements.
- **Expand / compile** may decompose a node into finer MetaCode nodes, then into machine code.
- Large systems: compile **by subtree** when needed; do not dump the whole monorepo into one run.

### 2.1 Essential components (what meta may / should cover)

| Component | Purpose |
|-----------|---------|
| Purpose / intent | Why the system exists |
| Architecture | Boundaries, modules, data flow |
| Surface | User-visible or API-visible interface |
| Behavior + tests | Same coin — features and how we know they work |
| Data / state | Entities, persistence, lifecycle |
| Infra | Runtime deps (DB, servers) only as needed |
| Non-goals / open questions | Stops fake precision |

---

## 3. Hard rules

### 3.1 Structure owns skeleton; model fills flesh

- Meta (and the compile process) owns **names, module graph, public surface, file layout**.
- The model **must not invent** new modules, public APIs, or layout that meta did not authorize.
- Bodies (algorithms, UI wiring details not fixed in meta) may be filled by the model under that skeleton.
- Prefer deterministic structure across recompiles; flesh need not be bit-identical.

### 3.2 Code and tests are one coin

- Specify production behavior and checks **together** under the same feature nodes where possible.
- Prefer minimal MetaCode vs MetaBDD split: tests largely fall out of the same description.
- **Elaborations allowed:** explicit always-on test cases; architecture choices not implied by features (prefer hierarchy over a parallel novel).

### 3.3 No redundancy

- State each requirement or rule **once**, at the right level of the tree.
- Refine in children; do not restate the same fact in siblings or parallel docs.

### 3.4 Embed, don’t doc-drift

- Machine code should carry meta intent via **naming and structure**, not hand-maintained parallel documentation.
- Docs as compile output are fine; docs as a second source of truth are not.

### 3.5 Simple as possible

- Prefer human-editable hierarchical Markdown (or equivalent) until formal grammar is justified.
- Closed-context skills implement compile/decompile before any custom parser/codegen engine.

---

## 4. Compile semantics

```text
compile(language_definition, metacode) → machine_code + tests + compile_report
```

**Allowed inputs:** this language definition; the MetaCode unit; the compile skill text.  
**Forbidden (greenfield):** ambient chat; unrelated repo files; full product SPEC; existing machine code.

**Compile must:**

1. Derive module/file/function (or UI component) names and layout from meta.  
2. Emit classic code + tests consistent with co-specified scenarios.  
3. Refuse or flag meta gaps rather than silently inventing structure.  
4. Produce a short **compile report**: assumptions, elaborations, conflicts, questions.

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
| 0.1-stub | Initial loadable def split from SPEC; expect rapid revision after first todo example loop |
