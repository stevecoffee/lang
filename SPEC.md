# lang — SPEC

**Status:** design / pre-MVP  
**Owner:** Steve  
**Working names:** MetaCode (language), MetaCompiler (compile step), MetaBDD / MetaTester (tests) — **better names TBD**  
**Keep work list:** `Meta coding language project` (`GKT:project`)

Living product contract for a fresh agent. This file is the authority for
**what** we are building and **what is out of scope**. Implementation layout,
tooling choices, and day-to-day commands will land in separate docs when the
MVP is scaffolded.

**Authority map**

| Need | Doc / surface |
|---|---|
| Living product contract | **this file (SPEC.md)** |
| Operational work list | Keep **`Meta coding language project`** (`GKT:project`; bind `[GKT:repo]` when remote exists) |
| Implementation / layout / tests | *not yet* (add `IMPLEMENTATION.md` when code lands) |
| Closed archaeology | *not yet* (add `HISTORY.md` as decisions close) |

---

## 1. Purpose

Create an **intermediate higher-level coding language** for the conceptual
space programmers already work in: progressive hierarchical description,
condensation, and analysis of software — not line-oriented source as the
primary artifact.

**Core reframe**

| Layer | Role |
|---|---|
| **Meta language** (MetaCode or successor name) | Primary authoring / design surface |
| **AI-assisted generation** | The *compile* step (MetaCompiler or successor) |
| **Classic code** (TypeScript, Python, …) | The new *machine language* — deterministic runtime target |

Compiling a MetaCode unit may mean **decomposing** it into finer MetaCode
units, then eventually into conventional code. Drift, conflicts, misalignment,
and redundancy across layers must be managed by automated process — not
manual doc sync.

**North star:** a small, real MVP where hierarchical meta-description compiles
into a type-checked or CLI-runnable conventional codebase, with tests that
follow the same compile strategy, and a path to **decompile** existing code
into the meta layer.

---

## 2. Guiding principles

| Principle | Meaning |
|---|---|
| **Hierarchy first** | Description, condensation, and analysis are progressive and nested — not flat file dumps of prose. |
| **Classic code is machine code** | Conventional languages remain the executable substrate; the meta layer does not replace runtimes. |
| **AI write = compile** | Generation into machine code is a *compile step* with deterministic naming and structure where possible; not free-form chat coding. |
| **Tests compile with the product** | MetaBDD / MetaTester uses the same strategy as MetaCode → machine code. Prefer deterministic behavior ⇒ deterministic tests. |
| **Minimal MetaCode vs MetaBDD split** | If compiled behavior is deterministic, required tests should largely fall out of the same description. |
| **Embed, don’t document-drift** | Prefer naming conventions and structural techniques so machine code carries meta intent; avoid docs that rot unless the compiler maintains them. |
| **MVP before prior-art capture** | Ship a first prototype before deep literature review so research informs, not freezes, the design. |
| **Language loop before chrome** | Voice UI, dashboards, multi-agent shells wait until compile / decompile / test loop exists. |
| **Refuse ambiguity in the toolchain** | Compiler and tooling should fail loudly on unresolved names, conflicts, and layer misalignment. |

---

## 3. Scope

### In scope

- **Language design** — hierarchical description, condensation, analysis; primary artifact is not line-oriented source.
- **Hierarchical compile** — MetaCode → finer MetaCode units → conventional code; greenfield and brownfield operational states.
- **Deterministic structure** — MetaCompiler-managed file / object / function naming where practical; AI fills machine-code bodies under that structure.
- **Decompile** — analysis and summary of existing codebases, test suites, and documentation into the meta layer (killer-app direction; may trail first greenfield MVP).
- **Testing & validation** — MetaTester / MetaBDD; standards for suite/plan execution and reporting, including human review of design and function.
- **Drift control** — automated handling of conflicts, misalignment, and redundancy across meta and machine layers.
- **MVP prototype** — e.g. a small real app (todo app is an acceptable first target); prefer type-checked or CLI-runnable targets.
- **Prior art (timed)** — research hierarchical disclosure / RLM-style decomposition and related work **after** first MVP is sketched or written, to avoid conceptual capture.
- **Naming** — replace working “Meta*” names when better ones exist.

### Out of scope (until language + compile/decompile/test loop exists)

- Keep reorg tooling and model bake-offs (other projects).
- Generic AI products, news, personal / health / home todos.
- Pure process notes with no language or toolchain implication.
- Product chrome: voice as first-class UI, coding/planning dashboards, Kanban shells, multi-agent company frameworks.
- Full harness / openclaw productization beyond what the MVP compile loop needs.

### Deferred but recorded (not blockers for MVP)

Ideas captured on the Keep list that may re-enter after the loop works:

- Hermes / openclaw-shaped agent project shell around the language.
- CLI or harness evolution of the compiler.
- Pulling techniques from “AI coding harness / techniques / ideas” notes.
- Voice and dashboard surfaces as *native* interfaces to the meta layer.

---

## 4. Problem framing

### What is broken today

Programmers and AI assistants already operate at a **conceptual** level
(intent, modules, contracts, tests) but author and review primarily at the
**machine** level (files, lines, diffs). That mismatch causes:

- Lossy translation from design → code and code → understanding.
- Drift between docs, tests, and implementation.
- AI coding that is powerful but **non-deterministic** as a “compile” step.
- Brownfield codebases that cannot be lifted into a maintainable higher
  description without heroic manual summary.

### What success looks like

1. An author can express a small system primarily in the meta language.
2. A compile step produces conventional code with stable structure and names.
3. Tests are produced or implied by the same description and run against the
   machine target.
4. Re-compile after meta edits is repeatable; conflicts surface explicitly.
5. (Later) An existing small codebase can be decompiled into editable meta
   form without losing critical behavior.

---

## 5. MVP definition

**MVP goal:** prove the **language + compile + test** loop on one small app.

| Slice | Acceptance sketch |
|---|---|
| **Meta source** | One hierarchical description of a tiny app (e.g. todo CLI or library) |
| **Compile** | Produces runnable / type-checked conventional code in a chosen target language |
| **Structure** | File/module layout and public names are compiler-controlled, not free-form model prose |
| **Tests** | At least one path where tests are generated or derived with the same pipeline and pass |
| **Re-run** | Second compile after a deliberate meta edit either succeeds cleanly or fails with a clear conflict report |
| **Non-goals for MVP** | Decompiler completeness, voice/UI, multi-language targets, production packaging |

**Suggested first prototype host:** small todo-style app (matches Keep note;
keeps domain out of the way of the language experiment).

**Target machine language:** choose one for MVP (TypeScript or Python preferred
for agent ergonomics); multi-target is post-MVP.

---

## 6. Architecture sketch (non-normative until implemented)

Conceptual pipeline only — not a commitment to package layout.

```
┌─────────────────┐     compile      ┌──────────────────┐     emit      ┌─────────────────┐
│  Meta source    │ ───────────────► │  Meta IR / plan  │ ────────────► │  Machine code   │
│  (hierarchy)    │                  │  (names, graph)  │   (+ AI fill) │  + tests        │
└────────▲────────┘                  └──────────────────┘               └────────┬────────┘
         │ decompile (later)                                                      │
         └────────────────────────────────────────────────────────────────────────┘
```

| Stage | Responsibility |
|---|---|
| **Parse / load** | Read hierarchical meta units; validate shape |
| **Plan** | Resolve names, module graph, public surface; detect conflicts |
| **Emit skeleton** | Deterministic files, signatures, test shells |
| **Fill** | AI (or templates) write bodies under the skeleton |
| **Verify** | Typecheck / test / report; refuse silent drift |
| **Decompile** | (Post-MVP) Lift machine code + signals back to meta |

Exact IR, file formats, and whether “fill” is mandatory vs template-only are
**open decisions** for the first implementation spike.

---

## 7. Open decisions

Track here until closed (then move rationale to HISTORY when that file exists).

| ID | Question | Notes |
|---|---|---|
| D1 | Final product / language name | Working: MetaCode / MetaCompiler / MetaBDD |
| D2 | MVP machine target (TS vs Python vs other) | Prefer one; agent-friendly |
| D3 | Meta source format (custom syntax vs structured markdown/YAML/JSON tree) | Must support hierarchy + tool edit |
| D4 | How much of compile is deterministic vs model-filled | Lean deterministic structure, model for bodies |
| D5 | Identity of meta units across recompiles | Stable IDs vs path-based names |
| D6 | First decompile scope | Whole repo vs module; how tests/docs feed in |
| D7 | Repo remote + Keep `[GKT:repo]` binding | Bind after `origin` exists |

---

## 8. Non-goals (standing)

- Replacing conventional languages or runtimes.
- A general chatbot or multi-agent “company” product.
- Guaranteeing correct AI-generated bodies without verify (typecheck/tests).
- Supporting every host language in v1.
- Perfect recovery of intent from arbitrary legacy code in v1.

---

## 9. Work list & process

- **Backlog / live todos:** Keep list **`Meta coding language project`**.
- **Done work:** reorder items into COMPLETED on that list (unchecked), per GKT
  consumer conventions — do not invent a second todo system in-repo until needed.
- **Contract changes:** edit this SPEC; keep scope meta on the Keep list in sync
  when in/out-of-scope boundaries move.
- **Agents:** prefer this SPEC + Keep list over inventing parallel plans.

---

## 10. Success metrics (directional)

| Signal | Direction |
|---|---|
| Meta → machine round-trip on MVP app | Works repeatedly |
| Time to change behavior via meta edit + recompile | Competitive with hand-editing machine code for the same change |
| Conflict/drift reports | Actionable; no silent overwrite of divergent machine edits (policy TBD) |
| Decompile (when started) | Readable meta that recompiles to behaviorally similar machine code |

---

## 11. Document history

| Date | Change |
|---|---|
| 2026-08-09 | Initial SPEC from Keep list `Meta coding language project` scope and backlog themes; repo initialized. |
