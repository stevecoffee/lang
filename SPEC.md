# lang — SPEC

**Status:** design / Phase 1 (language definition)  
**Owner:** Steve  
**Repo:** [github.com/stevecoffee/lang](https://github.com/stevecoffee/lang)  
**Working names:** MetaCode (language), MetaCompiler (compile step), MetaBDD / MetaTester (tests) — **better names TBD**  
**Keep work list:** `Meta coding language project` (`GKT:project`; `[GKT:repo] https://github.com/stevecoffee/lang`)

Living product contract. This file owns **thesis, principles, and phase scope**. Keep holds operational todos only (not a second copy of this contract).

**Authority map**

| Need | Doc / surface |
|---|---|
| Living product contract | **this file (SPEC.md)** |
| Source repository | [github.com/stevecoffee/lang](https://github.com/stevecoffee/lang) (`origin`) |
| Operational work list | Keep **`Meta coding language project`** — `gkt list find-by-repo` from this worktree |
| Implementation / layout / tests | *not yet* (`IMPLEMENTATION.md` when code lands) |
| Closed archaeology | *not yet* (`HISTORY.md` as decisions close) |

---

## 1. Purpose

Create an **intermediate higher-level coding language** (working name: MetaCode) that matches the **conceptual space programmers already operate in**: progressive hierarchical description, condensation, and analysis of software — not line-oriented source as the primary artifact.

**Thesis (keep this if you keep only one idea)**

> **Meta is source. AI write is compile. Classic code is machine language.**

That is not another prompt framework. It is a claim about **who owns structure** (the language / compile process) versus **who fills bodies** (the model), and about what programmers should author day to day.

| Layer | Role |
|---|---|
| **Meta language** (MetaCode or successor) | Primary authoring and design surface |
| **AI-assisted generation** | The *compile* step (MetaCompiler or successor) |
| **Classic code** (TS, Python, …) | The new *machine language* — executable substrate |

Compiling a meta unit may mean **decomposing** it into finer meta units, then into conventional code. Drift, conflicts, misalignment, and redundancy across layers must be managed deliberately (process first; automation later).

**Near-term posture:** define the language for **humans and LLMs**. Defer automated scripted tooling until the language is much better defined; formalize syntax and build compilers/decompilers after the essential components and features are locked. Compile/decompile remain real operations — first as disciplined human+LLM procedures, later as software.

---

## 2. Principles

### 2.1 Hierarchy as the unit of work

Progressive hierarchical description, condensation, and analysis is the right unit. Compile is **tree expansion** (and eventually emit to machine code), not free-form string generation.

Programmers already think in layers: system → package → module → function. Today’s tools force authoring at the bottom and hope the top stays true.

A meta “file” is not classic code with comments; it is a **node in a refinement tree**. Child nodes refine parents; condensation rolls detail upward without losing requirements.

### 2.2 Deterministic skeleton, non-deterministic flesh

**Structure owns names and layout; the model fills bodies.**

The compile process (later: MetaCompiler) deterministically manages file / object / function naming and graph layout; AI writes “machine code” under that structure. Greenfield and brownfield operational states are both required eventually.

Most AI coding fails operationally because structure is free-form: renames, file placement, and public APIs thrash between runs. If the compile process owns the graph and names, the model is a **backend for emit** (closer to a register allocator than a co-author). That ownership is also what makes recompile and drift detection possible later.

### 2.3 Tests as the same language

Production code and tests are **two sides of the same coin**. MetaCode should generally specify both at once. Prefer **minimal or no distinction** between MetaCode and MetaBDD / MetaTester: same strategy as meta → machine code; suite/plan running and reporting included; human review of design and function of both code and application remains in scope.

If meta implies behavior, tests should largely **fall out** of that description — not a second novel maintained in parallel. Hard check: if a meta edit cannot change both product and tests in one recompile (or one implement pass), they are not yet unified.

**Elaborations are allowed** where needed, e.g.:

- specific test cases that must always be included  
- architecture or design choices not implied by the feature description  

Some of that is addressable through hierarchical decomposition rather than a separate test language.

### 2.4 Embed meta in machine code without doc rot

Machine code should carry meta intent via **naming conventions and structural markers**, not hand-maintained parallel documentation. Documentation as **compile output** is fine; documentation as a second source of truth is not. This is the only durable path to brownfield and decompile without bitrot.

### 2.5 No redundancy

Redundancy is avoided at all costs. Duplicate statements of the same requirement or rule drift out of sync and raise maintenance cost. Say each fact once, at the right level of the tree; refine below rather than restating beside.

### 2.6 Simple as possible, but no simpler

Language and design stay minimal while still meeting the Phase 1 dual requirements (§3.1). Resist formal grammar, custom tooling, and product chrome until essentials are proven in use by humans and LLMs.

### 2.7 Prior art after a first baseline

Research prior art thoroughly, but **after** a first MVP / baseline is planned or written, to avoid conceptual capture. Hierarchical disclosure / RLM-style ideas may inform later; they do not define the language up front.

### 2.8 Language before chrome

Harness, dashboard, Kanban, voice UI, multi-agent shells, and related product surface wait until the language and the compile/decompile story are real enough to critique (§3.4).

---

## 3. Phases

Work **cycles** through phases and improves iteratively. A first full pass should produce a **baseline MVP** worth reasoning about and critiquing — not a finished product. Scripted automation is deferred until the language stabilizes; Phases 2–3 begin as human+LLM practice and become tools later.

### 3.1 Phase 1 — Language structure and definition

**Goal:** high-level language definition, file/system structure, and process overview — enough to author and critique real meta, without requiring custom scripts.

**Must cover (essential components):**

- code (behavior / implementation intent)  
- tests (same coin as code; see §2.3)  
- architecture  
- infrastructure where needed (databases, servers, other runtime deps)  

**Dual requirements**

1. **Clone fidelity:** capture enough detail to extract/decompile a project and recreate a **functionally identical clone with no code copied** (behavioral parity under a chosen suite — not paste, not mere prose summary).  
2. **Human editability:** the meta language is easy for a human to understand and edit (and usable by LLMs under the same conventions).

**Phase 1 deliverable shape (design, not toolchain):** written definition + structure/process overview + enough worked content that humans and LLMs can expand, condense, implement from, and lift into meta. Formal syntax and automated tooling come later.

**Also in Phase 1 design space:** working names may stay temporary; better product names than MetaCode / MetaCompiler are desirable but not a gate.

### 3.2 Phase 2 — Decompiler

**Goal:** lift existing systems into meta; prove the language against reality.

- Build decompiler capability and **test on existing projects** (first: LLM-assisted lift; later: scripted tooling).  
- Killer-app direction: analysis and summary of codebase, test suite, and existing documentation into editable meta — not a dead report.

Success implies meta that a later (or concurrent) compile pass can use toward a behavioral clone (§3.1 requirement 1).

### 3.3 Phase 3 — Compiler

**Goal:** emit conventional code (and tests) from meta; use with decompile to **rebuild an existing project as new, clean machine code**.

- Deterministic management of file / object / function naming and layout; AI writes machine-code bodies under that structure.  
- **Greenfield** and **brownfield** operational states.  
- Same pipeline strategy for tests as for product code (§2.3).  
- Prefer type-checked or CLI-runnable machine targets when choosing an early host language.

“Clean” means fit structure and maintainability under meta authority — success is still **behavior + tests + stable public surface**, not cosmetic reformatting alone.

### 3.4 Someday / maybe

Deferred until language + core loop earn them:

- full CLI or agent harness around the language  
- voice as a first-class native interface  
- coding/planning dashboard; Kanban-style UI  
- techniques mined from “AI coding harness / techniques / ideas” notes  
- broader openclaw / Hermes-style product shell (distinct from using a small app domain as an early example)

---

## 4. Scope summary

### In scope (product)

- Intermediate meta language for hierarchical description, condensation, analysis  
- Compile: meta → finer meta → classic machine code (+ tests), structure-led  
- Decompile: existing code / tests / docs → meta (killer-app path)  
- Drift, conflict, misalignment, redundancy control across layers (process now; automation later)  
- Human review of design and function in the validation story  
- Iterative phase loop toward a baseline MVP, then improvement  

### Out of scope (for now)

- Keep reorg tooling, model bake-offs, other projects’ concerns  
- Generic AI products, news, personal/health/home todos  
- Pure process notes with no language implication  
- Product chrome in §3.4 until the language loop exists  
- **Automated scripted toolchain** as a Phase 1 requirement (explicitly deferred)  
- Replacing conventional languages/runtimes; multi-host-language v1; perfect recovery of arbitrary legacy intent in v1  

---

## 5. Conceptual pipeline

Non-normative until implemented. Early on, stages may be human+LLM procedures.

```
┌─────────────────┐   compile    ┌──────────────────┐    emit     ┌─────────────────┐
│  Meta source    │ ───────────► │  Plan / skeleton │ ──────────► │  Machine code   │
│  (hierarchy)    │  (expand +   │  (names, graph)  │  (+ AI fill)│  + tests        │
└────────▲────────┘   structure) └──────────────────┘             └────────┬────────┘
         │ decompile                                                        │
         └──────────────────────── verify / reconcile ──────────────────────┘
```

| Stage | Responsibility |
|---|---|
| **Author / refine** | Humans and LLMs edit hierarchical meta |
| **Plan / skeleton** | Resolve names, module graph, public surface; detect conflicts |
| **Emit / fill** | Structure-led machine files + tests; model fills bodies |
| **Verify** | Types, tests, review; refuse silent drift when automation exists |
| **Decompile** | Lift machine code + tests + docs into meta |

---

## 6. Open decisions

| ID | Question | Notes |
|---|---|---|
| D1 | Final product / language name | Working: MetaCode / MetaCompiler / MetaBDD |
| D2 | First machine target (TS vs Python vs other) | Prefer one; agent-friendly; typecheck or CLI-runnable |
| D3 | Meta source format | Hierarchy + human/LLM edit first; formal grammar later |
| D4 | How much of compile is deterministic vs model-filled | Lean deterministic structure, model for bodies |
| D5 | Identity of meta units across revisions | Stable IDs vs path/title-based names |
| D6 | First decompile scope | Whole repo vs module; role of tests/docs |
| D7 | Repo remote + Keep `[GKT:repo]` | **Closed 2026-08-09:** `https://github.com/stevecoffee/lang` |
| D8 | When to introduce scripted tooling | After language essentials are stable and exemplified |

---

## 7. Work list & process

- **Contract (this file):** thesis, principles, phases, scope.  
- **Todos:** Keep **`Meta coding language project`** only — do not re-host the principles dump on the list.  
- **Done work on Keep:** reorder into COMPLETED (unchecked), per GKT consumer conventions.  
- **Scope boundary moves:** update this SPEC and the Keep `[GKT:list-scope]` meta when in/out-of-scope changes.  
- **Agents:** prefer this SPEC over inventing parallel plans; use Keep for live tasks.

---

## 8. Success signals (directional)

| Signal | Direction |
|---|---|
| Phase 1 | Meta for a real-ish system is human-editable and LLM-usable; covers code, tests, architecture (infra as needed) |
| Clone bar | Lift → re-implement yields functional parity without copying code |
| Unify tests | One meta change drives product and tests together |
| Phase 2 | Existing projects lift into meta that remains editable |
| Phase 3 | Meta emits clean machine code under deterministic structure; green and brown modes |
| Later | Drift/conflict handling is explicit; tooling automates without changing the language’s meaning |

---

## 9. Document history

| Date | Change |
|---|---|
| 2026-08-09 | Initial SPEC from Keep list; repo initialized. |
| 2026-08-09 | GitHub `stevecoffee/lang`; Keep `[GKT:repo]` bound; D7 closed. |
| 2026-08-09 | Absorbed Keep background, principles, and Phase 1–3 / someday detail; human+LLM-first posture; scripted tooling deferred (D8). Keep remains todos-only for this content. |
